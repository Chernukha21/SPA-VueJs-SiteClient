<template>
  <div class="content bar max">
    <center>
      <OrderList 
        v-if="choosen_page == 0" 
        :category_list="category_list" 
        :product_list="product_list"
      />
      <Catalog 
        v-if="choosen_page == 1"
        :category_list="category_list" 
        :product_list="product_list"
      />
    </center>
   </div>
</template>

<script>
import Catalog from './Catalog.vue'
import OrderList from './OrderList.vue'
export default {
  name: 'ContentBar',
  props: ['choosen_page', 'category_list', 'product_list'],
  data () {
    return {
      page: 0
    }
  },
  components: {
    Catalog,
    OrderList
  },
  methods: {
    getPage: function (id) {
      this.page = id
    },
    getProps: function () {
      // console.log(":", this.product_list)
    }
  },
  beforeMount () {
    this.getProps()

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .content.bar {
    width: 100%;
    padding-top: 122px;
    position: absolute;
    right: 0!important;
  }
  .content.bar.min {
    width: calc(100% - 280px);
  }
  .content.bar.max {
    width: calc(100% - 80px);
  }
</style>
