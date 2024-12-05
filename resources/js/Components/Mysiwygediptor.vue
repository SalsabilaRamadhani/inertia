<template>
    <div>
      <div ref="editor"></div>
    </div>
  </template>
  
  <script>
  import Quill from 'quill';
  import 'quill/dist/quill.snow.css';
  
  export default {
    name: 'WysiwygEditor',
    props: ['content'],
    emits: ['update:content'],
    mounted() {
      this.editor = new Quill(this.$refs.editor, {
        theme: 'snow',
      });
  
      this.editor.on('text-change', () => {
        this.$emit('update:content', this.editor.root.innerHTML);
      });
  
      if (this.content) {
        this.editor.root.innerHTML = this.content;
      }
    },
  };
  </script>
  