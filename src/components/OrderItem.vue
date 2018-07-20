<template>
	<div class="order item">
		<div class="layer n1 main info">
			<div class="columns">
				<img :src="getImageUri()"/>
			</div>
			<div class="columns">
				<p>{{ itemName }}</p>
				<p>{{ categoryName }}</p>
			</div>
			<div class="columns">
				<p>{{ date }}</p>
			</div>
			<div class="columns">
				<p>{{ price }}</p>
				<p>{{ count }}</p>
				<p>{{ sum }}</p>
			</div>
		</div>
		<div class="layer n2 status info">
			<StatusBar 
				:id="statusId"
				:name="statusName"
			/>
		</div>
	</div>
</template>

<script>
import StatusBar from './StatusBar.vue'
export default {
	name: 'OrderItem',
	data () {
		return {
			imageDefault: 'https://orig00.deviantart.net/379a/f/2011/298/2/5/180x180_px_v___2_0_by_skull_queen-d4dyoqb.jpg',
			imageUri: '',
			itemName: 'simple item',
			itemId: (this.info["ProductId"]) ? this.info["ProductId"] : 'p2',
			categoryName: 'simple category',
			categoryId: 'g2',
			statusId: (this.info["StageId"]) ? this.info["StageId"] : 1,
			statusName: 'in proce',
			date: (this.info["Date"]) ? this.info["Date"] : '2018-02-08',
			count: (this.info["Amount"] && this.info["Price"]) 
						? this.info["Amount"] / this.info["Price"] 
							: 4,
			price: (this.info["Price"]) ? this.info["Price"] : 20,
			sum: (this.info["Amount"]) ? this.info["Amount"] : 80
		}
	},
	props: ['info', 'category_list', 'status_list', 'product_list'],
	components: {
		StatusBar
	},
	methods: {
		getImageUri: function () {
			return (this.imageUri !== '') ? this.imageUri : this.imageDefault
			// console.log(this.info)
		},
		getProps: function () {
			// console.log(this.product_list)

		},
		getProductItemInfo: function (id) {
			let res = (this.product_list.filter(item => item["Id"] === id))[0]
			this.itemName = res["Caption"]
			this.categoryId = res["GroupId"]
			this.imageUri = res["Img"]
			res = "undefined"
		},
		getCategoryInfo: function (id) {
			let res = (this.category_list.filter(item => item["Id"] === id))[0]
			this.categoryName = res["Caption"]
			// console.log(res)
		},
		getStatusInfo: function (id) {
			let res = (this.status_list.filter(item => item["Id"] === id))[0]
			this.statusName = res["Caption"]
		}
	},
	beforeMount () {
	    this.getProductItemInfo(this.itemId)
	    this.getCategoryInfo(this.categoryId)
	    this.getStatusInfo(this.statusId)
	}
}
	
</script>

<style scoped>
	.order.item {
		width: 960px;
		margin: 25px auto;
		background-color: #f7f3f3;
	}
	.order.item .layer.n1 {
		padding: 8px;
		text-align: left;
		display: flex;
	}
	.order.item .layer.n1 > div {
		padding: 12px;
	}
	.order.item .layer.n2 {

	}
	.order.item .layer.n1 > div:nth-child(1) {
		width: 20%;
		border: 1px solid #e1cece;
	}
	.order.item .layer.n1 > div:nth-child(2) {
		width: 30%;
		border: 1px solid #e1cece;
	}
	.order.item .layer.n1 > div:nth-child(3) {
		width: 30%;
		border: 1px solid #e1cece;
	}
	.order.item .layer.n1 > div:nth-child(4) {
		width: 20%;
		border: 1px solid #e1cece;
	}
	
	img {
		width: 100px;
		height: 100px;
		margin: 5px;
	}
</style>