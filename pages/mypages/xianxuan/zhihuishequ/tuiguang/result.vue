<template>
	<view>
		<view class="" style="text-align: center;">
			<u-icon name="checkmark-circle-fill" label="提交成功,结果在24小时内回复" color="#2979ff" label-size="40" size="120" label-pos="bottom"></u-icon>
		</view>
		<u-gap></u-gap>
		<u-button type="success" @click="back">返回首页</u-button>
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
					url:'../zhihuishequ'
				})
			},
		}
	}
</script>

<style scoped>

</style>
