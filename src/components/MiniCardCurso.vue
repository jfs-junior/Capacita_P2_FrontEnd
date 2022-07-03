<template>
  <div>
    <q-img
      :src="url"
      style="width: 150px"
      ratio="1"
      spinner-color="white"
      class="rounded-borders cursor-pointer"
      @click='icon=true'
    >
      <div class="absolute-bottom text-center text-body2">
        {{ curso.nome_curso }}
      </div>
    </q-img>

    <!-- DETALHES DOS CURSOS -->
    <q-dialog v-model="icon">
      <q-card>
        <q-card-section class="row items-center q-pb-none">
          <q-space />
          <q-btn icon="close" flat round dense v-close-popup />
        </q-card-section>

        <q-card-section class="q-py-none">
          <div class="text-h5 text-center text-weight-bold">{{ curso.nome_curso }}</div>
          <div  class='q-py-md'><q-img :src="url"/></div>
          <p class="q-ma-none text-body1 text-justify">{{ curso.descricao }}</p><br>
          <p class="q-ma-none q-pa-none text-body1 text-weight-medium">Deficiência: <span class="text-italic">{{ curso.Tipo_deficiencium.nome }}</span></p>
          <p class="q-ma-none q-pa-none text-body1 text-weight-medium">Custo: <span class="text-weight-bolder">{{ curso.valor }}</span></p>
        </q-card-section>

        <q-card-section class="row items-center q-pb-lg">
          <q-space/>
          <q-btn flat round color="grey" icon="star" class="q-mr-sm" />
          <q-btn style="font-size: 0.8em;" rounded color="orange" label="Inscrever-se" @click="confirm = true"/>
        </q-card-section>
      </q-card>
    </q-dialog>

    <!-- DIALOG CONFIRMAÇÃO -->
    <q-dialog v-model="confirm" persistent>
      <q-card>
        <q-card-section class="text-center flex-center">
          <q-avatar icon="school" color="primary" text-color="white" /><br><br>
          <span class="q-ml-sm">
            Você deseja se inscriver em:<br><br>
            Curso: {{ curso.nome_curso }}<br>
            Instituição: {{ instituicao.nome }}<br>
            Valor: <span class="text-weight-bolder">{{ curso.valor}}</span>

          </span>
        </q-card-section>

        <q-card-actions align="center">
          <q-btn flat label="Cancelar" color="primary" v-close-popup />
          <q-btn flat label="Confirmar Inscrição" color="primary" class="text-weight-bold" v-close-popup @click="inscrever()"/>
        </q-card-actions>
      </q-card>
    </q-dialog>

    <!-- CONCLUSÃO INSCRIÇÃO -->
    <q-dialog v-model="alert">
      <q-card class="text-center">
        <q-card-section>
          <q-avatar :icon="alertMensage.icon" :color="alertMensage.cor" text-color="white" /><br><br>
        </q-card-section>

        <q-card-section class="q-pt-none">
          {{ alertMensage.mensagem }}
        </q-card-section>

        <q-card-actions align="center">
          <q-btn label="OK" color="white" text-color="black" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>

    <!-- MODAL DE CADASTRO PcD-->
    <q-dialog v-model="login">
      <q-card>
        <q-card-section class="row items-center q-pb-none">
          <q-space />
          <q-btn icon="close" flat round dense v-close-popup />
        </q-card-section>
      <Login @closeModal="login = false"/>
      </q-card>
    </q-dialog>

  </div>
</template>

<script>
import Login from 'components/Login'
export default {
  name: 'MiniCardCurso',
  data () {
    return {
      alert: false,
      icon: false,
      confirm: false,
      login: false,
      alertMensage: {
        icon: null,
        cor: null,
        mensagem: null
      },
      url: 'http://localhost:3000/imagens/' + this.curso.url_img
    }
  },
  components: {
    Login
  },
  props: {
    curso: {
      id: String,
      nome_curso: String,
      carga_horaria: String,
      deficiencia: String,
      resumo: String,
      descricao: String,
      valor: String,
      url_img: String,
      Instituicao: Object,
      Tipo_deficiencium: Object
    },
    instituicao: Object
  },
  methods: {
    inscrever () {
      const id = localStorage.getItem('idUsuario')
      let response = null

      const buscar = () => {
        const usuario = this.$axios.post('http://localhost:3000/usuario-busca', { id })
        return usuario
      }
      const logar = () => {
        this.login = true
      }
      const verificarLogin = () => {
        if (response.data.Usuario == null) {
          return false
        } else {
          return true
        }
      }
      const inscricao = async () => {
        const inscricao = {
          id_usuario_pcd: response.data.Usuario.Usuario_pcd.id,
          id_curso: this.curso.id
        }
        await this.$axios.post('http://localhost:3000/verificar_inscricao', inscricao).then(async response => {
          // SE INSCRIÇÃO NÃO EXISTIR, ENTÃO INSCREVER!
          if (response.data.liberado === true) {
            this.$axios.post('http://localhost:3000/inscricao', inscricao).then(responseInscricao => {
              console.log(response.data)
              console.log(responseInscricao.data)
              this.alertMensage.icon = 'thumb_up'
              this.alertMensage.mensagem = responseInscricao.data.message
              this.alertMensage.cor = 'secondary'
              this.alert = true
              this.icon = false
            }).catch(err => {
              console.log(err)
            })
          } else {
            console.log(response.data)
            this.alertMensage.icon = 'report_problem'
            this.alertMensage.mensagem = response.data.message
            this.alertMensage.cor = 'warning'
            this.alert = true
            this.icon = false
          }
        })
      }

      // EXECUTAR CADEIRA DE AÇÕES
      const execute = async () => {
        response = await buscar()
        if (verificarLogin()) {
          inscricao()
        } else {
          if (verificarLogin()) {
            inscricao()
          } else {
            logar()
          }
        }
      }
      execute()
    }
  }
}
</script>
