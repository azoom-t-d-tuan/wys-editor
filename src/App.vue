<template>
  <div id="app">
    <summernote
      class="form-control"
      name="summernote"
      :model="content"
      :config="config"
      v-on:change="
        (value) => {
          content = value
        }
      "
    />
  </div>
</template>

<script>
import Summernote from './components/summernote'

export default {
  name: 'App',
  components: {
    Summernote,
  },
  data() {
    return {
      content: null,
      config: {
        height: 230,
        toolbar: [
          // [groupName, [list of button]]
          ['style', ['bold', 'italic', 'underline', 'clear']],
          ['font', ['strikethrough', 'superscript', 'subscript']],
          ['fontsize', ['fontsize']],
          ['color', ['color']],
          ['para', ['ul', 'ol', 'paragraph']],
          ['insert', ['gxcode']], // plugin: summernote-ext-codewrapper
        ],
      },
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
