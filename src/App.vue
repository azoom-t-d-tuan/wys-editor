<template>
  <div id="app">
    <text-editor
      class="text-editor"
      v-model="content"
      :options="editorOptions"
    />
  </div>
</template>

<script>
import TextEditor from './components/text-editor'

export default {
  name: 'App',
  components: {
    TextEditor,
  },
  data() {
    return {
      content: '',
      editorOptions: {
        modules: {
          toolbar: [['bold', 'italic', 'underline', 'strike'], ['blockquote']],
        },
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
}
.text-editor {
  height: 375px;
  width: 50%;
  margin: 0 auto;
}
</style>
