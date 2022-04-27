<template>
  <div
    id="app"
    :class="{ 'active': isMenuVisible }">
    <!-- Menu toggle -->
    <a
      href="#menu"
      id="menuLink"
      class="menu-link"
      @click='isMenuVisible = !isMenuVisible'>
      <!-- Hamburger icon -->
      <span></span>
    </a>

    <div id="menu">
      <TheSideMenu @class-selected='setClass'/>
    </div>

    <div id="main">
      <TheClassMainContent :classData='classData' />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      classData: {},
      isMenuVisible: false
    }
  },
  methods: {
    setClass(data) {
      this.classData = data
    }
  }
}
</script>
