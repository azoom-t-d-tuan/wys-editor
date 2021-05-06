<script>
import $ from 'jquery'
import 'summernote/dist/summernote-lite.min.js'
import 'summernote/dist/summernote-lite.min.css'
export default {
  name: 'summernote',
  props: {
    model: {
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    config: {
      type: Object,
      default: () => ({}),
    },
  },
  mounted() {
    let vm = this
    let config = this.config

    config.callbacks = {
      onInit: function() {
        $(vm.$el).summernote('code', vm.model)
      },

      onChange: function() {
        vm.$emit('change', $(vm.$el).summernote('code'))
      },

      onBlur: function() {
        vm.$emit('change', $(vm.$el).summernote('code'))
      },
    }

    $(this.$el).summernote(config)
  },
}
</script>
<template>
  <textarea id="editor" :name="name"></textarea>
</template>
