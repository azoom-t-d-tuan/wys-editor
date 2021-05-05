<template>
  <div id="app">
    <quill-editor
      ref="myQuillEditor"
      class="quill-editor"
      v-model="value"
      :options="editorOption"
      @change="$emit('update:content', value)"
    />
  </div>
</template>

<script>
import 'quill/dist/quill.core.css'
import 'quill/dist/quill.snow.css'
import 'quill/dist/quill.bubble.css'
import { Quill, quillEditor } from 'vue-quill-editor'

const fonts = ['roboto', 'arial', 'meiryo']
const Font = Quill.import('attributors/style/font')
Font.whitelist = fonts
Quill.register(Font, true)

export default {
  name: 'TextEditor',
  components: { quillEditor },
  props: {
    content: String
  },
  data() {
    return {
      value: '',
      editorOption: {
        modules: {
          toolbar: [
            [{ font: fonts }, { size: ['small', false, 'large', 'huge'] }],
            ['font', 'bold', 'italic', 'underline', 'strike'],
            ['image', 'link'],
            [{ align: [] }],
            [{ list: 'ordered' }, { list: 'bullet' }],
            [{ indent: '-1' }, { indent: '+1' }],
          ],
        },
        placeholder: 'Type here...',
        theme: 'snow',
      },
    }
  },
}
</script>

<style>
.ql-snow .ql-picker.ql-font .ql-picker-label[data-value='roboto']::before,
.ql-snow .ql-picker.ql-font .ql-picker-item[data-value='roboto']::before {
  content: 'Roboto';
  font-family: 'Roboto';
}

.ql-snow .ql-picker.ql-font .ql-picker-label[data-value='arial']::before,
.ql-snow .ql-picker.ql-font .ql-picker-item[data-value='arial']::before {
  content: 'Arial';
  font-family: 'Arial';
}

.ql-snow .ql-picker.ql-font .ql-picker-label[data-value='meiryo']::before,
.ql-snow .ql-picker.ql-font .ql-picker-item[data-value='meiryo']::before {
  content: 'Meiryo';
  font-family: 'Meiryo';
}

.ql-font-arial {
  font-family: 'Arial';
}

.ql-font-roboto {
  font-family: 'Roboto';
}

.ql-font-meiryo {
  font-family: 'Meiryo';
}
</style>
