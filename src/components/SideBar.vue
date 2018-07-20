<template>
  <div class="side bar" :class="{max: max, max: min}">
    <ul>
      <li @click="getOrder">Order</li>
      <li @click="getSideBar">Catalog</li>
    </ul>
    <div class="mdl-button mdl-js-button mdl-button--raised mdl-js-ripple-effect" @click="myFilter()">>></div>
  </div>
</template>

<script>
export default {
  name: 'SideBar',
  data () {
    return {
      title: 'Catolog',
      max: false,
      min: true
    }
  },
  methods: {
    getOrder: function () {
      // console.log('get Order')
      this.$emit('pageSelect', 0)
    },
    getSideBar: function () {
      // console.log('get Side')
      this.$emit('pageSelect', 1)
    },
    myFilter: function () {
      this.min = !this.min
      this.max = !this.max
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .side.bar {
    background-color: grey;
    height: calc(100% - 122px);
    position: fixed;
    top: 123px;
  }
  .side.bar.max {
    width: 200px;
  }
  .side.bar.min {
    width: 80px;
  }
  .side.bar ul {
    list-style: none;
    padding: 0;
    margin: 20px;
  }
  .side.bar ul li {
    cursor: pointer;
  }
  .side.bar.max ul li {
    font-size: 2em;
    padding-bottom: 4px;
  }
  .btn {
    position: fixed;
    left: 60px;
    bottom: 50px;
  }
</style>
