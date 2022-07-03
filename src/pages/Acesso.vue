<template>
  <q-page>
    <div>
      <Login @closeModal="sair()" />
    </div>
  </q-page>
</template>

<script>
import Login from 'components/Login'
export default {
  name: 'Acesso',
  components: {
    Login
  },
  methods: {
    sair () {
      window.location = '/'
    }
  }
}
</script>
