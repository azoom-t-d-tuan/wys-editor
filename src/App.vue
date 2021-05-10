<template>
  <div id="app">
    <summernote
      class="form-control"
      name="summernote"
      :model="content"
      :config="config"
      @change="
        (value) => {
          content = value;
        }
      "
    />
  </div>
</template>

<script>
import Summernote from "./components/summernote.vue";
export default {
  name: "App",
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
          ["style", ["bold", "italic", "underline", "clear"]],
          ["font", ["strikethrough", "superscript", "subscript"]],
          ["fontsize", ["fontsize"]],
          ["fontname", ["fontname"]],
          ["table", ["table"]],
          ["insert", ["link", "picture", "video", "hr"]],
          ["color", ["color"]],
          ["para", ["ul", "ol", "paragraph"]],
          "undo",
          "redo",
        ],
        fontNames: [
          "Arial",
          "Arial Black",
          "Comic Sans MS",
          "Courier New",
          "Merriweather",
          "Roboto",
        ],
        fontNamesIgnoreCheck: ["Merriweather", "Roboto"],
        placeholder: "Write here...",
      },
    };
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@100&display=swap');
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
