<template>
	<view>
		<!-- 房源图片、房源名称、建筑面积、房源单价、房源类型、房源介绍 -->
		<view class="house">
			<u-image width="100%" height="400rpx" :src="baseUrl+house.pic"></u-image>
			<view class="housetext">
				<h3>{{house.sourceName}}</h3>
				<text>建筑面积:{{house.areaSize}}㎡</text>
				<text>房源单价:{{house.price}}</text>
				<text>房源类型:{{house.houseType}}</text>
				<text>房源介绍:{{house.description}}</text>
			</view>
		</view>
		<view class="back">
			<u-button type="success" @click="back">展示主页</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				house:''
			}
		},
		methods: {
			back(){
				uni.navigateBack({
					delta:1
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/house/housing/'+this.id)
				this.house=res1.data
				console.log(res1);
			},
		},
		onLoad(ops) {
			this.id=ops.id
			this.getData()
		}
	}
</script>

<style scoped>
	.housetext{
		display: flex;
		flex-direction: column;
	}
	.house{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx #aaa solid;
	}
	.back{
		width: 90%;
		position: fixed;
		bottom: 20rpx;
		right: 36rpx;
	}
</style>
