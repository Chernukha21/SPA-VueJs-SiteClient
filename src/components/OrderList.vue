<template>
	<div>
		<OrderItem 
			v-for="order in orders" 
			:info="order" 
			:key="order.etag"
			:category_list="category_list"
			:product_list="product_list"
			:status_list="statuses"
		/>
	</div>
</template>

<script>
	import axios from 'axios'
	import OrderItem from './OrderItem'

	export default {
	  name: 'OrderList',
	  props: ['category_list', 'product_list'],
	  data () {
	  	return {
	  		content: 'some content of OrderList',
	  		orders: [],
	  		statuses: []
	  	}
	  },
	  components: {
	  	OrderItem
	  },
	  methods: {
	  	getOrders: function () {
	  		axios.get('http://localhost:3000/order/list/').then(response => {
	  			this.orders = JSON.parse(response.data.d)
	  			// console.log(this.orders)
	  		})
	  	},
	  	getStatuses: function () {
	  		axios.get('http://localhost:3000/order/status/list/').then(response => {
	  			this.statuses = JSON.parse(response.data.d)
	  			// console.log(this.statuses)
	  		})
	  	}
	  },
	  beforeMount () {
	    this.getStatuses()
	    this.getOrders()
	  }
	}
</script>

<style scoped>
	
</style>