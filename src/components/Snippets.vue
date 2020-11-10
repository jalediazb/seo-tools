<template>
<div class="column is-full">
  <div class="card">
    <header class="card-header has-background-link">
      <p class="card-header-title has-text-white">Vista Preliminar Títulos</p>
    </header>
    <div class="card-content">
      <div class="content">
        <div class="field">
          <p class="control has-icons-left">
            <input v-model="inputTitle" @keyup="contarPixeles()" id="input-title" class="input" type="text">
            <span class="icon is-small is-left">
              <span id="count" class="is-size-7">
                125
              </span>
            </span>
          </p>
        </div>
        <p id="breadcrumb">Hola</p>
        <p id="titulo" class="has-text-link">
          <span v-if="inputTitle === 'Título...'">Este es un título de prueba</span>
          <span v-else-if="inputTitle === ''">-</span>
          <span v-else>{{ inputTitle }}</span>
        </p>
        <p id="description">Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
      </div>
    </div>
  </div>
</div>
</template>
<script>
export default {
  name: 'Snippets',
  data() {
    return {
      inputTitle: "Título...",
    }
  },
  computed: {
    
  },
  methods: {
    contarPixeles() {
      let titleText = document.getElementById('titulo');
      console.log(titleText);
    }
  }
}
</script>
<style scoped>
</style>
