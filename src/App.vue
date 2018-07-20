<template>
  <div id="app" class="mdl-layout mdl-js-layout mdl-layout--fixed-header">
    <Header :page_title="current_page"/>
    <SideBar  @pageSelect="choosenPage"/>
    <ContentBar 
                  :choosen_page="current_page" 
                  :product_list="product_list"
                  :category_list="category_list"
                />
    <h1>{{getCategory()}}</h1>

  </div>
</template>

<script>


import Header from './components/Header.vue'
import ContentBar from './components/ContentBar.vue'
import SideBar from './components/SideBar.vue'
import axios from 'axios'

export default {
  name: 'App',
  data () {
    return {
      current_page: 1,
      product_list: [],
      category_list: []
    }
  },
  components: {
    Header,
    SideBar,
    ContentBar
  },
  methods: {
    choosenPage: function (page) {
      this.current_page = page
      // console.log(this.current_page)
    },
    getProduct: function () {
      axios.get('http://localhost:3000/product/list').then( response => {
        this.product_list = JSON.parse(response.data.d)
        // console.log(this.product_list)
      })
    },
    getCategory: function () {
      axios.get('http://localhost:3000/category/list').then( response => {
        this.category_list = JSON.parse(response.data.d)
        // console.log(this.category_list)
      })
    }
  },
  beforeMount () {
    this.getCategory()
    this.getProduct()
  }
}
</script>

<style>
  body {
    margin: 0;
  }
</style>
