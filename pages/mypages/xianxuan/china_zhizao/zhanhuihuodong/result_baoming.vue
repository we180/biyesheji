<template>
	<view>
		<view class="icon" style="text-align: center;margin: 20rpx;">
			<u-icon name="checkmark-circle-fill" color="#2977ff" label="报名成功" size="120" label-pos="bottom" label-size="50"></u-icon>
		</view>
		<view class="back">
			<u-button type="primary" @click="back">返回主页</u-button>
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
					url:'../china_zhizao'
				})
			},
		}
	}
</script>

<style>

</style>
