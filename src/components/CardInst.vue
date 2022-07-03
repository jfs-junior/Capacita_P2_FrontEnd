<template>
  <div>
    <!-- INICIO CARD INSTITUIÇÃO -->
    <q-card class="my-card shadow-6 q-ma-sm">
      <q-img :src="url"/>

      <q-card-section>

        <div class="row no-wrap items-center">
          <div class="col text-h6 ellipsis">
            {{ instituicao.nome_instituicao}}
          </div>
        </div>

      </q-card-section>

      <q-card-section class="q-pt-none">
        <div class="text-body2 text-grey">
          <p>{{ instituicao.descricao }}</p>
        </div>
      </q-card-section>

      <div class="absolute-bottom">
        <q-separator />

        <q-card-actions class="flex justify-end">
          <q-btn flat color="primary" icon="add_circle" padding="xs">
            <div class="q-pa-xs" @click="icon = true">Informações</div>
          </q-btn>
        </q-card-actions>
      </div>
    </q-card>

    <!-- DETALHES DA INSTITUIÇÃO -->
    <q-dialog v-model="icon">
      <q-card>
        <q-card-section class="row items-center q-pb-none">
          <q-space />
          <q-btn icon="close" flat round dense v-close-popup />
        </q-card-section>

        <q-card-section class="q-py-none">
          <div class="text-h5 text-center text-weight-bold">{{ instituicao.nome_instituicao }}</div>
          <div  class='q-py-md'><q-img :src="url"/></div>
          <p class="q-ma-none text-body1 text-justify">{{ instituicao.descricao }}</p><br>
          <p>Alguns Cursos:</p>
        </q-card-section>

        <q-card-section class="row justify-center items-center q-pb-lg q-gutter-sm">
          <div v-for="curso in instituicao.Cursos" :key="curso.id">
            <MiniCardCurso :curso='curso' :instituicao='instituicao' />
          </div>
        </q-card-section>
      </q-card>
    </q-dialog>
  </div>
</template>

<script>
import MiniCardCurso from 'components/MiniCardCurso'
export default {
  name: 'CardInstituicao',
  data () {
    return {
      stars: 4,
      icon: false,
      url: 'http://localhost:3000/imagens/' + this.instituicao.url_img,
      icon2: false
    }
  },
  props: {
    instituicao: Object
  },
  components: {
    MiniCardCurso
  }
}
</script>

<style  scoped>
.my-card {
  width: 290px;
  height: 407px;
}

p {
    display: -webkit-box;
    -webkit-line-clamp: 8;
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
    text-align: justify;
}
</style>
