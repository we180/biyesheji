<template>
	<view>
		<view class="" style="display: flex;justify-content: center;">
			<uqrcode ref="code"></uqrcode>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		},
		onReady() {
			this.$refs.code.make({
				text:'11451419190810',
				size:100
			})
		}
	}
</script>

<style scoped>

</style>
