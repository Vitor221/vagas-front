<template>
  <div>
    <vagas-favoritas></vagas-favoritas>
    <topo-padrao @navegar="component = $event" />
    <alerta v-if="exibirAlerta"/>
    <conteudo v-if="visibilidade" :conteudo="component"></conteudo>
  </div>
</template>

<script>
import Conteudo from '@/components/layouts/Conteudo.vue'
import TopoPadrao from '@/components/layouts/TopoPadrao.vue'
import VagasFavoritas from '@/components/comuns/VagasFavoritas.vue'
import Alerta from '@/components/comuns/Alerta.vue'

export default {
  name: 'App',
  data: () => ({
    visibilidade: true,
    component: 'Home',
    exibirAlerta: false
  }),
  components: {
    Conteudo,
    TopoPadrao,
    VagasFavoritas,
    Alerta
  },
  mounted() {
    this.emitter.on('alerta', () => {
      this.exibirAlerta = true
      setTimeout(() => this.exibirAlerta = false, 4000)
      console.log('Apresentar a mensagem de alerta customizada')
    })
  }
}
</script>

<style scoped></style>
