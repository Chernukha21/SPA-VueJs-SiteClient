<template>
	<div class="category main">
		<center>
			<h4>{{ name }}</h4>
		</center>
		<div class="category content">
			<Description :info="info" v-if="open == 0"/>
			<div v-if="open == 1" class="category show case">
				<Product 
					v-for="product in product_list" 
					v-if="product['GroupId'] == info['Id']"
					:info="product"
				/>
			</div>
		</div>
	</div>
</template>

<script>
import Description from './Description.vue'
import Product from './Product.vue'
export default {
	name: 'Category',
	data () {
		return {
			name: (this.info["Caption"]) ? this.info["Caption"] : 'Category Name',
			id: (this.info["Id"]) ? this.info["id"] : 'g1',
			open: 1,
			contain_: []
		}
	},
	props: ['info', 'product_list'],
	components: {
		Product,
		Description
	},
	methods: {
		getContainItems: function (id) {
			// if (this.product_list.length > 0) {
				// this.contain_.push(this.product_list.filter(item => item["GroupId"] === id))
				// console.log("+:", this.product_list)
			// }

			// let i = this.product_list.filter(item => item["GroupId"] === id)
			// console.log(this.product_list)
		}
	},
	afterMount () {
		// this.getContainItems(this.id)
		// console.log(this.product_list)
	}
}
</script>

<style scoped>
	.category.main {
		width: 960px;
		margin: 20px auto;
		background-color: #f7f3f3;
	}
	.category.show.case {
		width: 100%;
	}

</style>