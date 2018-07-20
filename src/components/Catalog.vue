<template>
	<div class="catalog ">
		<Category 
			v-for="category in category_list"
			:info="category"
			:product_list="product_list"
		/>
	</div>
</template>

<script>
	import Category from './Category.vue'
	export default {
		name: 'Catalog',
		props: ['category_list', 'product_list'],
		data () {
			return {
				content: "Catalog"
			}
		},
		components: {
			Category
		},
		beforeMount () {
			// this.getContainItems(this.id)
			// console.log(this.product_list)
		},
		afterMount () {
			if ((this.product_list).length > 0) {
				// console.log(":", this.product_list)
			}
		}
	}
</script>

<style scoped>
	.catalog{
		display: grid;

	}
</style>