<template>
  <header>
    <atom-search />
    <NuxtLink to="/">Home page</NuxtLink>
    <NuxtLink to="/filter">Filter page</NuxtLink>
  </header>
</template>
<script>
export default {
  name: 'Header',

  data() {
    return {
      expand: false,
    }
  },

  methods: {
    toggle() {
      this.expand = true
      return (this.expand = !this.expand)
    },
    filterTitleActivity() {
      const oldQuery = this.$router.query;
      return this.expand
        ? this.$router.push({
            name: 'ProductFilter',
            query: { ...oldQuery, title: this.keywords },
          })
        : null
    },
  },
}
</script>
<style lang="scss" scoped>
header {
  display: flex;
  height: 90px;
  justify-content: center;
  align-items: center;
  background: #297eff;
}
</style>