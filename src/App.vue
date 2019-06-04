<template>
  <div id="app">
    <auto-textarea v-model="inputValue"></auto-textarea>
  </div>
</template>

<script>
  import AutoTextarea from './components/AutoTextarea.vue'

  export default {
    name: 'app',
    components: { AutoTextarea },
    data () {
      return {
        inputValue: ''
      }
    }
  }
</script>

<style lang="scss">
  * {
    box-sizing: border-box;
  }

  #app {
    padding: 50px;
  }
</style>
