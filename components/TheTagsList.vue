<template>
  <div class="chips-container p-t-15 p-b-15">
    <span 
      v-for='(tag, index) in tags'
      :key='index'
      class="chip m-r-10 m-b-10 pure-button">
      <div class="chip-content">{{ tag }}</div>
    </span>
  </div>
</template>

<script>
export default {
  props: {
    tags: {
      type: Array,
      required: false,
      default: () => ([])
    }
  }
}
</script>

<style lang="scss" scoped>
.chip {
  display: inline-flex;
  flex-direction: row;
  border: none;
  cursor: pointer;
  height: 36px;
  outline: none;
  padding: 0;
  font-size: 14px;
  font-color: #333333;
  font-family: "Open Sans", sans-serif;
  white-space: nowrap;
  align-items: center;
  border-radius: 16px;
  vertical-align: middle;
  text-decoration: none;
  justify-content: center;
}
.chip-content {
  cursor: inherit;
  display: flex;
  align-items: center;
  user-select: none;
  white-space: nowrap;
  padding-left: 12px;
  padding-right: 12px;
}
</style>