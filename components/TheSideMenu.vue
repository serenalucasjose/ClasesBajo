<template>
  <div class="pure-menu">
    <form class="pure-form">
      <input
        v-model="query"
        type="search"
        autocomplete="off"
        class="pure-input w-full"
        placeholder="Busqueda"/>
    </form>
    <ul class="pure-menu-list">
      <li 
        v-for="({ title }, index) in filteredClases"
        :key='index'
        class="pure-menu-item">
        <a
          href="#home"
          class="pure-menu-link"
          @click.stop='handleOnClick(filteredClases[index])'>
          {{ title }}
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
const fields = ['slug', 'title', 'media', 'body', 'description', 'tags']

export default {
  async fetch() {
    this.cachedClases = await this.$content('clases')
      .sortBy('title')
      .only(fields)
      .fetch()
      .catch((err) => {
        error({ statusCode: 404, message: 'Page not found' })
      })

    this.filteredClases = this.cachedClases
    // Set default class
    this.handleOnClick(this.cachedClases[0])
  },
  watch: {
    async query (query) {
      this.filteredClases = (!query) ? this.cachedClases : await this.$content('clases')
        .sortBy('title')
        .only(fields)
        .search(query)
        .fetch()
    }
  },
  data() {
    return {
      filteredClases: [],
      cachedClases: [],
      query: ''
    }
  },
  methods: {
    handleOnClick(data) {
      this.$emit('class-selected', data)
    }
  }
}
</script>

<style lang="scss" scoped>
</style>