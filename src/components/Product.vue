<template>
	<div class="product item">
		
			<p>{{ title }}</p>
			<p><img :src="getImageUri()"/></p>
		
	</div>
</template>

<script>
export default {
	name: 'Proguct',
	data () {
		return {
			title: (this.info["Caption"]) ? this.info["Caption"] : 'Proguct title',
			imageDefault: 'https://orig00.deviantart.net/379a/f/2011/298/2/5/180x180_px_v___2_0_by_skull_queen-d4dyoqb.jpg',
			imageUri: (this.info["Img"]) ? this.info["Img"] : ''
		}
	},
	props: ['info'],
	methods: {
		getImageUri: function () {
			return (this.imageUri !== '') ? this.imageUri : this.imageDefault
		}
	}
}
</script>

<style scoped>
	.product.item {
		width: 200px;
		height: 200px;
		margin: 5px;
		display: inline-block;
		background-color: #fff;
	}
	img {
		width: 100px;
		height: 100px;
	}
</style>