<template>
	<!-- 店家图片、店家名，评分，月销量 -->
	<view>
		<view class="dianjialist">
			<view class="dianjia" v-for="(item,dianjialistid) in dianjialist" :key="dianjialistid" @click="todetails(dianjialistid)">
				<image :src="baseUrl+item.imgUrl" mode=""></image>
				<view class="dianjiaindex">
					<h3>{{item.sellerName}}</h3>
					<text>评分:{{item.score}}</text>
					<text>月销量:{{item.saleQuantity}}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				dianjialist:[],
				
			}
		},
		methods: {
			todetails(id){
				uni.navigateTo({
					url:'shop_details?id='+this.dianjialist[id].sellerId
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/takeout/collect/list')
				this.dianjialist=res1.rows
				console.log(res1);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.dianjia image{
		width: 220rpx;
		height: 220rpx;
	}
	.dianjia{
		display: flex;
		flex-direction: row;
		margin: 10rpx;
		padding: 10rpx;
		box-shadow: 8rpx 8rpx 16rpx gray;
		border-radius: 20rpx;
		border: #A0CFFF 2rpx solid;
	}
	.dianjiaindex{
		display: flex;
		flex-direction: column;
		margin-left: 20rpx;
	}
</style>
