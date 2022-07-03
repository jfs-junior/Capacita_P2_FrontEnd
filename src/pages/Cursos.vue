<template>
  <q-page padding>
    <div>
      <h4 class="text-center text-weight-bolder color-primary q-ma-lg text-azul_escuro">CURSOS</h4>
      <h5 class="text-center text-weight-bold q-ma-none q-mb-lg text-azul_escuro">Cursos em Destaque</h5>
      <p class="text-center " style="font-size: 1.5em;">Nossa missão é trazer para você os melhores cursos profissionalizantes. Através de uma rede de instituições de ensino, sua Capacitação estará garantida para o mercado de trabalho. </p>

      <!-- BARRA DE PESQUISAS -->
      <div class="q-px-md" align="center">
        <div class="row" style="max-width: 950px">
          <q-select
            outlined
            v-model="model"
            :options="options"
            label="Filtro"
            dense
            round
            class="q-pa-none col-xs-5 col-sm-2"
          />
          <q-input
            outlined
            bottom-slots
            v-model="pesquisa"
            label="Pesquisar"
            maxlength="50"
            round
            :dense="dense"
            class="q-pa-none col-xs-7 col-sm-10"
            @keyup.enter="pesquisar()"
            @keyup.esc="listar(); pesquisa = ''"
          >
            <template v-slot:append>
              <q-icon v-if="pesquisa !== ''" name="close" @click="pesquisa = ''; listar()" class="cursor-pointer" />
              <q-icon name="search" class="cursor-pointer" color="primary" @click='pesquisar()'/>
            </template>
          </q-input>
        </div>
      </div>

      <!-- ABAS -->
      <div class="q-pa-md flex justify-center">
        <div class="q-gutter-y-md" style="max-width: 950px;">
          <q-card>
            <q-tabs
              v-model="tab"
              inline-label
              class="bg-primary text-white shadow-2"
            >
              <q-tab name="cursos" icon="menu_book" label="Cursos" style="width: 100%" @click="model = 'Cursos'"/>
              <q-tab name="instituicoes" icon="apartment" label="Instituições"  style="width: 100%" @click="model = 'Instituições'"/>
            </q-tabs>

            <q-separator />

            <q-tab-panels v-model="tab" animated>
              <q-tab-panel name="cursos" class="flex justify-center">
                <div v-for="curso in cursos" :key="curso.id">
                  <CardCurso :curso="curso"/>
                </div>
              </q-tab-panel>

              <q-tab-panel name="instituicoes" class="flex justify-center">
                 <div v-for="instituicao in instituicoes" :key="instituicao.id">
                  <CardInst :instituicao="instituicao"/>
                </div>
              </q-tab-panel>
            </q-tab-panels>
          </q-card>
        </div>
      </div>
      <!-- FOOTER -->
    <div class="footer">
      <div class="q-pa-md q-px-xl row justify-center">
        <!-- LOGO -->
      <div class="logorodape" >
        <div class="col-xs-12 col-sm-2 flex justify-center ">
          <div class="q-pb-xl" style="width: 300px;">
            <q-img src="../imagens/logo_capacita_branca.png"/>
          </div>
        </div>
      </div>
        <!-- Coluna 1 -->
        <div class="col-xs-12 col-sm-2 flex justify-center">
          <div style="width: 100px;">
            <p><span>CAPACITA</span><br><br>
            <a href="#">Sobre Nós</a><br>
            <a href="#">Notícias</a><br>
            <a href="#">Contato</a></p>
          </div>
        </div>
        <!-- Coluna 2 -->
        <div class="col-xs-12 col-sm-2 flex justify-center">
          <div style="width: 100px;">
             <p><span>ENSINO</span><br><br>
              <a href="#">Cursos</a><br>
              <a href="#">Instituições</a><br>
              <a href="#">Fórum</a><br></p>
          </div>
        </div>
        <!-- Coluna 3 -->
        <div class="col-xs-12 col-sm-2 flex justify-center">
          <div  style="width: 100px;">
            <p>
              <span>ACESSO</span> <br><br>
              <a href="#">Cadastro</a> <br>
              <a href="#">Login</a>
            </p>
          </div>
        </div>
          <!-- BOTÕES -->
          <div class="col-xs-12 col-sm-2 flex justify-center">
            <div style="width: 120px;" class="q-gutter-y-sm">
              <q-btn color="orange" label="Registrar" style="width: 100px;"/>
              <q-btn color="white" text-color="orange" label="Entrar"  style="width: 100px"/>
            </div>
          </div>
        </div>
        <!-- COPY RIGHT -->
        <hr style="width: 90%; opacity: 30%">
        <p class="text-center q-mb-none q-pa-sm">© Copyright 2020</p>
      </div>
    </div>
  </q-page>
</template>

<script>
import CardCurso from 'components/CardCurso'
import CardInst from 'components/CardInst'
export default {
  name: 'PaginaCursos',
  mounted () {
    this.listar()
  },
  data () {
    return {
      tab: 'cursos',
      pesquisa: '',
      ph: '',
      model: 'Cursos',
      options: [
        'Cursos', 'Instituições'
      ],
      dense: true,
      cursos: null,
      instituicoes: null
    }
  },
  components: {
    CardCurso,
    CardInst
  },
  methods: {
    listar () {
      this.$axios.get('http://localhost:3000/curso').then(response => {
        this.cursos = response.data
      })
      this.$axios.get('http://localhost:3000/instituicao').then(response => {
        this.instituicoes = response.data
      })
    },
    pesquisarCurso () {
      var busca = {
        pesquisa: this.pesquisa
      }
      this.$axios.post('http://localhost:3000/curso-pesquisa', busca).then(response => {
        this.cursos = response.data
      })
    },
    pesquisarInstituicao () {
      var busca = {
        pesquisa: this.pesquisa
      }
      this.$axios.post('http://localhost:3000/instituicao-pesquisa', busca).then(response => {
        this.instituicoes = response.data
      })
    },
    pesquisar () {
      if (this.model === 'Cursos') {
        this.pesquisarCurso()
        this.tab = 'cursos'
      } else {
        this.pesquisarInstituicao()
        this.tab = 'instituicoes'
      }
    }
  }
}
</script>

<style lang="stylus">
//FOOTER
div.footer {
  padding-top: 2%;
  width: 100%;
  background-color: $primary;
}
.footer p span {
  color: orange;
  font-weight:600;
}
.footer{
font-size: 20px;
}
.footer a {
  text-decoration: none;
  color: #ffffff;
}
.footer a:hover {
  color: $azul_escuro;
  font-weight: 800;
}
</style>
