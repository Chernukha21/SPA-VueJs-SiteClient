<template>
  <header class="mdl-layout__header">
      <center>
        <h1>{{ getTitle(page_title) }}</h1>
      </center>
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: ['page_title'],
  data () {
    return {
      title: 'Catalog'
    }
  },
  methods: {
    getTitle: function (id) {
      switch (id) {
        case 0:
          this.title = 'Order List'
          break
        case 1:
          this.title = 'Catalog'
          break
        default:
          this.title = 'Order List'
      }
      return this.title
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  header {
    position: fixed;
  }

</style>
