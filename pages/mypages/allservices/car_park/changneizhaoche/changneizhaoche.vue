<template>
	<view>
		<view class="input">
			<u-field label="车牌号" v-model="carnum"></u-field>
			<u-button type="primary" @click="show=1">找车</u-button>
		</view>
		<view class="info" v-if="show==1">
			<!-- 停车场名称、地址、车位号 -->
			<h3>停车场名称:金辉大厦停车场</h3>
			<text>地址:金辉大厦</text>
			<text>车位号:23号</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				show:0,
				carnum:''
			}
		},
		methods: {
			
		}
	}
</script>

<style scoped>
	.info{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
		display: flex;
		flex-direction: column;
	}
</style>
