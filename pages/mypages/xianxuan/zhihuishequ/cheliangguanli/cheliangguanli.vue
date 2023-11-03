<template>
	<view>
		<view class="carlist">
			<view class="car" v-for="(item,index) in shequcar_list" :key="index" @click="changecar(index)">
				<!-- 车牌号码、车位号、停车卡号、车主姓名、车主手机号、相关住户姓名和地址 -->
				<h3 style="margin: 10rpx;">车牌号码:{{item.carnum}}</h3>
				<text>车位号:{{item.stopnum}}</text>
				<text>停车卡号:{{item.stopcard}}</text>
				<text>车主姓名:{{item.carname}}</text>
				<text>车主手机号:{{item.carphone}}</text>
				<text>相关住户姓名:{{item.username}}</text>
				<text>地址:{{item.address}}</text>
			</view>
		</view>
		<view class="addcar">
			<u-button type="success" @click="toaddcar">添加车辆信息卡</u-button>
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
			toaddcar(){
				uni.navigateTo({
					url:'addcar'
				})
			},
			changecar(index){
				uni.navigateTo({
					url:'changecar?id='+index
				})
			},
		}
	}
</script>

<style scoped>
	.addcar{
		position: fixed;
		bottom: 0rpx;
		width: 100%;
		padding: 20rpx;
	}
	.car{
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border: #A0CFFF 2rpx solid;
		border-radius: 20rpx;
	}
</style>
