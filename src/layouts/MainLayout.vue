<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar class="relative-position" style="height: 62px;">
        <!-- BARRA DE TÍTULO -->
        <q-toolbar-title align="center">
          <div  class="row items-center">
            <div class="col">
              <!-- <p style="margin: 0; line-height: 1em;"><span class="text-weight-bold" style="letter-spacing: 0.4em;">CAPACITA</span><br><span style="font-size: 0.8em;">Cursos Inclusivos </span></p> -->
              <q-img src="../imagens/lg_capacita.svg" style="width: 180px" />
            </div>
          </div>
        </q-toolbar-title>
        <!-- BOTÃO DE MENU -->
        <div class="absolute-left" style="width: 100%; height: 62px;">
          <div class="float-left" style="padding: 7px 0 0 20px;">
            <q-btn
              style="font-size: 1.5em; border-radius: 0.5em;"
              dense
              icon="menu"
              aria-label="Menu"
              @click="leftDrawerOpen = !leftDrawerOpen"
            />
          </div>
          <!-- ICONE E BOTÃO DE ACESSO -->
          <div>
            <div class="float-right" style="height: 62px; padding: 6px 10px 0px 0;"><q-icon name="home" style="font-size: 3.5em;"/></div>
            <div class="float-right gt-xs" style="height: 62px; padding: 17px 15px 0 0;"><q-btn style="font-size: 1em;" rounded color="orange" label="Acesso" @click="icon = true"/></div>
          </div>
        </div>
      </q-toolbar>
    </q-header>
    <!-- MENU LATERAL -->
    <q-drawer
      v-model="leftDrawerOpen"
      overlay
      bordered
      elevated
      content-class="bg-grey-1"
    >
      <q-list>
        <div>
          <q-item>
            <q-item-label header class="text-orange-8 text-weight-bold" size="2em" style="font-size: 2em;">
              MENU
            </q-item-label>
            <q-item-section>
              <a href="#" align="right" style="text-decoration: none;"><q-icon name="closer" size="2em" rounded flat  dense @click="leftDrawerOpen = !leftDrawerOpen"/></a>
            </q-item-section>
          </q-item>
        </div>
        <div class="row">
          <div class="row col-12 texto-menu link-primario">
              <a href="/">
                <img  class="col-6 q-ml-lg q-my-sm" src="../imagens/btn_inicio.svg" alt="Botão de Inicial" style="width: 2.4em; vertical-align: middle;">
                <span class="col-6 q-ml-md">Início </span>
              </a>
          </div>
          <div class="row col-12 texto-menu link-primario">
              <a href="/sobrenos">
                <img  class="col-6 q-ml-lg q-my-sm" src="../imagens/btn_sobre_nos.svg" alt="Botão de Inicial" style="width: 2.4em; vertical-align: middle;">
                <span class="col-6 q-ml-md">Sobre Nós </span>
              </a>
          </div>
          <div class="row col-12 texto-menu link-primario">
              <a href="/cursos">
                <img  class="col-6 q-ml-lg q-my-sm" src="../imagens/btn_cursos.svg" alt="Botão de Inicial" style="width: 2.4em; vertical-align: middle;">
                <span class="col-6 q-ml-md">Cursos </span>
              </a>
          </div>
          <div class="row col-12 texto-menu link-primario">
              <a href="/noticias">
                <img  class="col-6 q-ml-lg q-my-sm" src="../imagens/btn_noticias.svg" alt="Botão de Inicial" style="width: 2.4em; vertical-align: middle;">
                <span class="col-6 q-ml-md">Notícias </span>
              </a>
          </div>
          <div class="row col-12 texto-menu link-primario">
              <a href="/">
                <img  class="col-6 q-ml-lg q-my-sm" src="../imagens/btn_forum.svg" alt="Botão de Inicial" style="width: 2.4em; vertical-align: middle;">
                <span class="col-6 q-ml-md">Fórum </span>
              </a>
          </div>
          <div class="row col-12 texto-menu link-primario">
              <a href="#" @click="icon = true; leftDrawerOpen = !leftDrawerOpen" >
                <img  class="col-6 q-ml-lg q-my-sm" src="../imagens/btn_acesso.svg" alt="Botão de Inicial" style="width: 2.4em; vertical-align: middle;">
                <span class="col-6 q-ml-md">Acesso </span>
              </a>
          </div>
          <div class="row col-12 texto-menu link-primario">
              <a href="/contato">
                <img  class="col-6 q-ml-lg q-my-sm" src="../imagens/btn_contatos.svg" alt="Botão de Inicial" style="width: 2.4em; vertical-align: middle;">
                <span class="col-6 q-ml-md">Contato </span>
              </a>
          </div>
        </div>
      </q-list>
    </q-drawer>

    <!-- MODAL DE CADASTRO PcD-->
    <q-dialog v-model="icon">
      <q-card>
        <q-card-section class="row items-center q-pb-none">
          <q-space />
          <q-btn icon="close" flat round dense v-close-popup />
        </q-card-section>
       <Login @closeModal="icon = false"/>
      </q-card>
    </q-dialog>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>

import Login from 'components/Login'
export default {
  name: 'MainLayout',
  components: {
    Login
  },
  data () {
    return {
      leftDrawerOpen: false,
      icon: false
    }
  }
}
</script>
