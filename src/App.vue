<template>
  <div id="app">
    <notifications></notifications>
    <section class="refactor">
      <h2>Refactor</h2>
      <textarea v-model="content" class="box" @change="handleChange"></textarea>
    </section>
    
    <section class="preview">
      <h2>Preview</h2>
      <vue-markdown :source="content" class="box" data-markdown-box="1"></vue-markdown>
      <div class="btn-wrapper">
        <button @click="copy">Copy HTML to Clipboard</button>
      </div>
    </section>
  </div>
</template>

<script>
import VueMarkdown from 'vue-markdown'
import 'normalize.css'
export default {
  name: 'App',
  components: {
    VueMarkdown
  },
  data(){
    return {
      content: localStorage.getItem('content') || ''
    }
  },
  methods: {
    handleChange(){
      localStorage.setItem('content', this.content)
    },
    copy(){
      const elem = document.querySelector('.box[data-markdown-box="1"]')
      navigator.clipboard.writeText(elem.innerHTML)
      this.$notify({
        type: 'success',
        text: 'Copied to Clipboard!'
      })
    }
  },
}
</script>

<style lang="scss">
#app {
  font-size: 16px;
  box-sizing: border-box;
  display: flex;
  grid-gap: 2rem;
  padding: 1rem;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
.refactor, .preview{
  flex: 1 1 0;
  display: flex;
  flex-direction: column;
  grid-gap: 0.5rem;
  h2{
    height: 50px;
    flex-basis: 50px;
  }

  .box{
    flex-grow: 1;
    min-height: 200px;
    height: auto;
    border: 1px solid black;
    border-radius: .5rem;
    resize: vertical;
    padding: .5rem;

  }
  textarea.box{
    margin-bottom: 2rem;
  }
  .btn-wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
</style>
