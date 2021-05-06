<template>
  <div class="quill-editor">
    <slot name="toolbar"></slot>
    <div ref="editor"></div>
  </div>
</template>

<script>
import 'quill/dist/quill.core.css'
import 'quill/dist/quill.snow.css'
import 'quill/dist/quill.bubble.css'
import Quill from 'quill'

const defaultOptions = {
  theme: 'snow',
  boundary: document.body,
  modules: {
    toolbar: [
      ['bold', 'italic', 'underline', 'strike'],
      ['blockquote', 'code-block'],
      [{ header: 1 }, { header: 2 }],
      [{ list: 'ordered' }, { list: 'bullet' }],
      [{ script: 'sub' }, { script: 'super' }],
      [{ indent: '-1' }, { indent: '+1' }],
      [{ direction: 'rtl' }],
      [{ size: ['small', false, 'large', 'huge'] }],
      [{ header: [1, 2, 3, 4, 5, 6, false] }],
      [{ color: [] }, { background: [] }],
      [{ font: [] }],
      [{ align: [] }],
      ['clean'],
      ['link', 'image', 'video'],
    ],
  },
  placeholder: 'Insert text here ...',
  readOnly: false,
}
export default {
  props: {
    value: {
      type: String,
      default: '',
    },
    options: {
      type: Object,
      required: false,
      default: () => ({}),
    },
  },
  data() {
    return {
      editor: null,
    }
  },
  mounted() {
    if (this.$el) {
      // Instance
      this.editor = new Quill(this.$refs.editor, {
        ...defaultOptions,
        ...this.options,
      })

      // Update model when text changes
      this.editor.on('text-change', () => this.update())
    }
  },
  beforeDestroy() {
    this.editor = null
    delete this.editor
  },
  methods: {
    update() {
      const html =
        this.editor.getText() && this.editor.root.innerHTML !== '<p><br></p>'
          ? this.editor.root.innerHTML
          : ''
      this.$emit('input', html)
    },
  },
}
</script>
