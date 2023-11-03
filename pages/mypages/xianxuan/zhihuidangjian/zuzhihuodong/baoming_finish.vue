<template>
	<view>
		<view style="text-align: center;">
			<u-icon name="checkmark-circle-fill" color="#2f69ff" label="报名成功" label-pos="bottom" size="120" label-size="40"></u-icon>
			<u-gap></u-gap>
			<u-button type="success" @click="back">返回首页</u-button>
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
			back(){
				uni.redirectTo({
					url:'../zhihuidangjian'
				})
			},
		}
	}
</script>

<style>

</style>
