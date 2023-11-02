<template>
	<view>
		<view class="head" style="text-align: center;margin: 10rpx;">
			<h2>评估结果为:</h2>
			<h1 style="color: #1890FF;">二级护理</h1>
			<u-gap></u-gap>
			<text>根据您填写的身体状况，您所需要的护理等级是二级护理</text>
		</view>
		<u-gap></u-gap>
		<view class="res">
			<text>老人日常基本需求，伙食，房间，定期换洗衣物床被，督促服药定期检查等</text>
			<h4>基础费用：3000元/月</h4>
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
			
		}
	}
</script>

<style scoped>
	.res{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: #A0CFFF solid 2rpx;
	}
</style>
