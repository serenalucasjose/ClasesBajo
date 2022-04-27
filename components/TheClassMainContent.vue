 <template>
  <div>
    <div class="header">
      <h1>{{ theTitle }}</h1>
      <h2>{{ theDescription }}</h2>
    </div>
    <div class="content">
      <!-- Chips -->
      <TheTagsList :tags='theTags' />
      <nuxt-content :document="classData" />
      <div class="pure-g">
        <TheMediaContent :classData='classData' />
      </div>
      <TheContentFooter />
    </div>
  </div>
</template>
 
<script>
export default {
  props: {
    classData: {
      type: Object,
      required: false
    }
  },
  computed: {
    mediaFiles() {
      return this.classData?.media || []
    },
    theTitle() {
      return this.classData?.title || ''
    },
    theDescription() {
      return this.classData?.description || ''
    },
    theTags() {
      return this.classData?.tags?.split(',') || []
    }
  }
}
</script>
 
<style lang="scss" scoped>
</style>