<template>
  <div class="column is-full">
    <div class="card">
      <header class="card-header has-background-link">
        <p class="card-header-title has-text-white">
          Vista Preliminar Google Snippets
        </p>
      </header>
      <div class="card-content">
        <div class="content">
          <div class="field">
            <label class="label">Título</label>
            <p class="control mb-1">
              <input
                v-model="inputTitle"
                @keyup="contarPixelesTitulo()"
                id="input-title"
                class="input"
                :class="colorInput"
                type="text"
              />
            </p>
            <p class="is-size-7">
              Pixeles: <span>{{ largoTitle }}</span> - Caracteres:
              <span>{{ caracteresTitulo }}</span>
            </p>
          </div>
          <div class="field">
            <label class="label">Descripción</label>
            <div class="control">
              <textarea
                class="textarea"
                :class="colorTextarea"
                id="textarea-description"
                v-model="textareaDescription"
              ></textarea>
            </div>
            <p class="is-size-7">
              Caracteres: <span>{{ caracteresDescription }}</span>
            </p>
          </div>
          <hr />
          <p id="breadcrumb">
            es-es.facebook.com › Lugares › La Coruña › Librería
          </p>
          <p id="titulo" class="has-text-link">
            <span class="max-600" v-if="inputTitle === ''">-</span>
            <span class="max-600" v-else>{{ inputTitle }}</span>
          </p>
          <p id="description">
            <span v-if="textareaDescription.length < 158">{{
              textareaDescription
            }}</span>
            <span v-else>{{ descripcionRecortada }}</span>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Snippets",
  mounted() {
    this.contarPixelesTitulo();
  },
  data() {
    return {
      inputTitle: "Título Preliminar de un Artículo...",
      largoTitle: 0,
      textareaDescription:
        'Esta es una teórica meta etiqueta "description". Según parámetros establecidos por Google debe tener una longitud aproximada de 920 pixels o 158 caracteres',
    };
  },
  methods: {
    contarPixelesTitulo() {
      let titleText = document.querySelector("#titulo span");
      this.largoTitle = titleText.offsetWidth;
    },
  },
  computed: {
    caracteresDescription() {
      return this.textareaDescription.length;
    },
    caracteresTitulo() {
      return this.inputTitle.length;
    },
    colorInput() {
      return this.largoTitle > 599
        ? "is-danger"
        : this.largoTitle < 400
        ? "is-warning"
        : "is-success";
    },
    colorTextarea() {
      return this.textareaDescription.length > 158
        ? "is-danger"
        : this.textareaDescription.length < 130
        ? "is-warning"
        : "is-success";
    },
    descripcionRecortada() {
      return this.textareaDescription.substring(0, 155) + "...";
    },
  },
};
</script>
<style scoped>
#breadcrumb,
#description {
  font-size: 14px;
  font-family: Arial, sans-serif;
  margin-bottom: 0;
}
#titulo {
  font-size: 20px;
  font-family: Arial, sans-serif;
  margin-bottom: -8px;
}
.max-600 {
  display: inline-block;
  overflow: hidden;
  max-width: 600px;
  text-overflow: ellipsis;
  white-space: nowrap;
}
</style>
