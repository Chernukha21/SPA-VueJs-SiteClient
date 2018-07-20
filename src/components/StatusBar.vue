<template>
	<div class="status bar">
		<div class="line">
			<div class="part n1" :class="{ active: isActive[0] }">{{ (id == 's1') ? name : '' }}</div>
			<div class="part n2" :class="{ active: isActive[1] }">{{ (id == 's2') ? name : '' }}</div>
			<div class="part n3" :class="{ active: isActive[2] }">{{ (id == 's3') ? name : '' }}</div>
			<div class="part n4" :class="{ active: isActive[3] }">{{ (id == 's4') ? name : '' }}</div>
			<div class="part n5" :class="{ active: isActive[4] }">{{ (id == 's5') ? name : '' }}</div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'StatusBar',
	data () {
		return {
			_name: (this.name) ? this.name : 'Done',
			_id: (this.id) ? this.id : 's1',
			isActive: [false, false, false, false, false]


		}
	},
	props: ['name', 'id'],
	methods: {
		addActivity: function (id) {
			let index = parseInt(id)
			this.isActive[index] = true
			console.log(index)
		}
	},
	afterMount  () {
		this.addActivity(this.id)
	}
}
</script>

<style scoped>
	.status.bar .line {
		width: 80%;
		height: 22px;
		margin: 8px auto;
		background-color: #bebebe;
		display: flex;
	}
	.status.bar .line .part {
		width: calc(20% - 1px);
		border-right: 1px solid #f7f3f3;
		flex: 1;
	}
	.status.bar .line .part:last-child {
		width: 20%;
		border-right: none;
	}
	.status.bar .line .part.active {
		background-color: #999393;
	}
</style>