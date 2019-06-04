<template>
  <div class="textarea">
    <textarea v-model="currentValue" :style="inputStyle"></textarea>
    <textarea class="shadow" v-model="currentValue" ref="shadow" tabindex="0"></textarea>
  </div>
</template>

<script>
  export default {
    name: 'AutoTextarea',
    props: {
      value: String
    },
    data () {
      return {
        currentValue: '',
        inputHeight: '0'
      }
    },
    watch: {
      currentValue () {
        this.resize()
        this.$emit('input', this.currentValue)
      }
    },
    computed: {
      inputStyle () {
        return {
          'min-height': this.inputHeight
        }
      }
    },
    mounted () {
      this.resize()
    },
    methods: {
      resize () {
        this.inputHeight = `${this.$refs.shadow.scrollHeight}px`
      }
    }
  }
</script>

<style scoped lang="scss">
  .textarea {
    textarea {
      padding: 8px;
      border: 1px solid #aeaeae;
      resize: none;
      overflow: hidden;
      font-size: 16px;
      height: 0;

      &.shadow {
        max-height: 0;
        pointer-events: none;
        opacity: 0;
        margin: 0;
      }
    }
  }
</style>