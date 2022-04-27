<template>
<div
  class="modal"
  :class="{ 'is-visible': isVisible }">
  <div class="modal__inner">
    <button
      class="modal__close"
      @click.stop='handleClick'>
    </button>
    <div class="modal-content h-full">
      <div class="pure-g h-full">
        <!-- Audio/Video -->
        <div class="pure-u-5-5 iframe-wrapper">
          <iframe
            v-if='fileCanBeShown(filePath)'
            :src="filePath"
            frameborder="0">
          </iframe>
        </div>
        <!-- CTA -->
        <div class="pure-u-5-5 cta-wrapper">
          <a
            class="pure-button pure-button-primary"
            :href='filePath'
            download>
            Descargar
          </a>
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<script>
  export default {
    props: {
      filePath: {
        type: String,
        required: false,
        default: ''
      },
      isVisible: {
        type: Boolean,
        required: true,
        default: false
      }
    },
    methods: {
      handleClick() {
        this.$emit('modal-close')
      },
      fileFormat(str) {
        const [,, format] = str.split('.')
        
        return format
      },
      fileCanBeShown(str) {
        const valid = ['pdf', 'wav', 'mp3', 'mp4']

        return valid.includes(this.fileFormat(str))
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>