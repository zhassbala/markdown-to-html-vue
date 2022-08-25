<template>
  <div id="app">
    <section class="refactor">
      <h2>Refactor</h2>
      <textarea v-model="content" class="box"></textarea>
    </section>
    
    <section class="preview">
      <h2>Preview</h2>
      <vue-markdown :source="content" class="box"></vue-markdown>
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
      content: ''
    }
  }
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
}
</style>
