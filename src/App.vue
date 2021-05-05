<template>
  <div id="app" class="page-container">
    <text-editor :content.sync="textContent" />
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
      textContent: '',
    }
  },
}
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.quill-editor {
  height: 375px;
  width: 50%;
  margin: 0 auto;
}
</style>
