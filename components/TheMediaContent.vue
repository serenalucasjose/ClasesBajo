<template>
  <div class="pure-u">
    <button
      v-for="(file, index) in media"
      :key='index'
      class="pure-button pure-button-primary m-r-25 m-b-25"
      :title='btnData(file)[1]'
      @click.stop='handleClick(file)'>
      {{ btnData(file)[0] }}
    </button>
    <!-- Media Modal -->
    <TheMediaModal
      :filePath='filePath'
      :isVisible='isModalVisible'
      @modal-close='isModalVisible = false'/>
  </div>
</template>

<script>
export default {
  props: {
    classData: {
      type: Object,
      required: false,
      default: () => ({})
    }
  },
  data() {
    return {
      filePath: '',
      isModalVisible: false
    }
  },
  computed: {
    media() {
      return this.classData?.media
    }
  },
  methods: {
    btnData(str) {
      return str.split('.')
    },
    handleClick(uri) {
      const { classData: { title } } = this 
      const fullPath = `./clases_bajo_media/${title}/${uri}`
      
      this.filePath = fullPath
      this.isModalVisible = true
    }
  }
}
</script>

<style lang="scss" scoped>
</style>