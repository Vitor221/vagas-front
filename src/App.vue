<template>
  <div>
    <vagas-favoritas></vagas-favoritas>
    <topo-padrao @navegar="component = $event" />

    <alerta v-if="exibirAlerta" :tipo="alerta.tipo">
      <template v-slot:titulo>
        <h5>{{ alerta.titulo }}</h5>
      </template>
        <p>{{ alerta.descricao }}</p>
    </alerta>

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
    exibirAlerta: false,
    alerta: { titulo: '', descricao: '', tipo: ''}
  }),
  components: {
    Conteudo,
    TopoPadrao,
    VagasFavoritas,
    Alerta
  },
  mounted() {
    this.emitter.on('alerta', (mensagemAlerta) => {
      this.alerta = mensagemAlerta
      console.log(this.alerta)
      this.exibirAlerta = true
      setTimeout(() => this.exibirAlerta = false, 4000)
    })
  }
}
</script>

<style scoped></style>
