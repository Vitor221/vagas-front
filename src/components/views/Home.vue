<template>
  <div class="container py-4">
    <div class="row">
      <div class="col">
        <pesquisar-vaga/>
      </div>
    </div>

    <div class="row mt-5">
      <div class="col-4">
        <indicador />
      </div>

      <div class="col-4">
        <indicador />
      </div>

      <div class="col-4">
        <indicador />
      </div>
    </div>
  </div>
</template>

<script>
import Indicador from '@/components/comuns/Indicador.vue'
import PesquisarVaga from '@/components/comuns/PesquisarVaga.vue'

export default {
  name: 'Home',
  components: {
    PesquisarVaga,
    Indicador
  },
    activated() {
    console.log('Componente é ativado')
    },
    deactivated() {
      console.log('Componente é desativado')
    },
      beforeUnmount() {
    console.log('Antes de demonstar/destruir')
    },
    unmounted() {
      console.log('Demonstado/destruído')
    },
    created() {
    console.log('Criado')
    },
}
</script>

<style scoped>

</style>
