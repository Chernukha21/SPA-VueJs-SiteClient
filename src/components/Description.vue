<template>
	<div class="category description">
		{{ content }}
	</div>
</template>

<script>
export default{
	name: 'Description',
	props: ['info'],
	data () {
		return {
			categoryId: 'g1',
			content: 'Some content description about current category.'
		}
	}
}
</script>

<style>
</style>