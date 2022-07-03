<template>
<div>
  <!-- TELA DE LOGIN -->
  <div v-show="logar == true" class="row q-pa-lg q-pb-xl flex-center">
    <div class="col-12 text-center">
      <h4 class="q-ma-lg txt-azul_escuro">ACESSO</h4>
    </div>
    <div class="col-xs-11 col-sm-8 col-md-8">
      <q-input type="email" bottom-slots v-model="email" label="E-mail" lazy-rules>
        <template v-slot:prepend>
          <q-icon name="alternate_email" />
        </template>
      </q-input>

      <q-input type="password" bottom-slots v-model="senha" label="Senha" @keyup.enter="login(email, senha)" >
        <template v-slot:prepend>
          <q-icon name="vpn_key" />
        </template>
      </q-input>
      <p><a href="#" class="link-primario text-azul_escuro">Esqueceu a Senha?</a></p>

      <div class="flex justify-center q-gutter-sm q-pt-lg q-ma-sm">
        <q-btn class="btn-fixed-width" rounded color="primary" label="Entrar"  @click="login(email, senha)"/><br>
        <q-btn class="btn-fixed-width" rounded color="primary" label="Inscreva-se" @click="$router.replace('inscricaopcd')"/><br>
        <q-btn class="btn-fixed-width" rounded color="primary" label="Solicitar Parceria" @click="$router.replace('inscricaoinst')"/>
      </div>
    </div>
  </div>

  <!-- TELA DE USUARIO LOGADO -->
  <div v-show="logar == false" class="row q-pa-lg q-pb-xl flex-center">
    <div class="col-12 text-center">
      <h4 class="q-ma-lg txt-azul_escuro">ACESSADO</h4>
    </div>
    <div class="col-sm-8 col-md-8">
      <q-input type="email" filled bottom-slots v-model="email" label="E-mail" disable readonly lazy-rules>
        <template v-slot:prepend>
          <q-icon name="alternate_email" />
        </template>
      </q-input>

      <q-input type="text" filled bottom-slots v-model="nome" label="Nome" disable readonly>
        <template v-slot:prepend>
          <q-icon name="account_circle" />
        </template>
      </q-input>

      <div class="flex justify-center q-gutter-sm q-pt-lg q-ma-sm">
        <q-btn class="btn-fixed-width" rounded color="red-5" label="Sair"  @click="sair()"/><br>
        <q-btn class="btn-fixed-width" rounded color="primary" label="Continuar" @click="fechar()"/><br>
      </div>
    </div>

  </div>

</div>
</template>

<script>
export default {
  name: 'LoginAcesso',
  data () {
    return {
      email: '',
      nome: '',
      senha: '',
      logar: false
    }
  },
  beforeMount () {
    if (localStorage.getItem('idUsuario') == null) {
      this.logar = true
    } else {
      this.logar = false
      console.log(localStorage.getItem('idUsuario'))
      this.email = localStorage.getItem('email')
      this.nome = localStorage.getItem('nome')
    }
  },
  methods: {
    login (email, senha) {
      const login = { email, senha }
      this.$axios.post('http://localhost:3000/usuario-login', login).then(response => {
        if (response.data.usuarioPcd != null) {
          console.log(response.data)
          this.$q.notify({
            color: 'green-4',
            textColor: 'white',
            icon: 'cloud_done',
            message: 'Usuário Pcd: ' + response.data.usuarioPcd.nome + ' CONNECTADO!'
          })
          localStorage.clear()
          localStorage.setItem('idUsuario', response.data.usuario.id)
          localStorage.setItem('email', response.data.usuario.email)
          localStorage.setItem('nome', response.data.usuarioPcd.nome)
          this.$emit('closeModal')
        } else if (response.data.instituicao != null) {
          console.log('Instituicao')
          this.$q.notify({
            color: 'green-4',
            textColor: 'white',
            icon: 'cloud_done',
            message: 'Instituicão: ' + response.data.instituicao.nome + ' CONNECTADA!'
          })
          localStorage.clear()
          localStorage.setItem('idUsuario', response.data.usuario.id)
          localStorage.setItem('email', response.data.usuario.email)
          localStorage.setItem('nome', response.data.instituicao.nome)
          this.$emit('closeModal')
        } else if (response.data.admin != null) {
          console.log('Admin')
          this.$q.notify({
            color: 'green-4',
            textColor: 'white',
            icon: 'cloud_done',
            message: 'Administrador Conectado.'
          })
          localStorage.clear()
          localStorage.setItem('idUsuario', response.usuario.id)
          localStorage.setItem('email', response.data.usuario.email)
          localStorage.setItem('nome', response.data.admin.nome)
          this.$emit('closeModal')
        } else {
          console.log(response.data.message)
          this.$q.notify({
            color: 'red-5',
            textColor: 'white',
            icon: 'cloud_done',
            message: response.data.message + '!'
          })
        }
      }).catch(err => {
        console.log(err)
      })
    },
    sair () {
      localStorage.clear()
      this.fechar()
    },
    fechar () {
      this.$emit('closeModal')
    }
  }
}
</script>

<style>
  .btn-fixed-width {
    width: 200px
  }

  .link_recuperacao {
    text-decoration: none;
  }
</style>
