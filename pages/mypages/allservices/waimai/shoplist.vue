<template>
	<view>
		<view class="search">
			<u-search :placeholder="keyword" @custom="search" @search="search"></u-search>
		</view>
		<view class="near">
			<view class="nearlist" v-for="(item,shoplist) in shoplist" :key="shoplist" @click="todetails(shoplist)">
				<view class="nearimg">
					<image :src="baseUrl+item.imgUrl" mode=""></image>
				</view>
				<view class="neartext">
					<h3>{{item.name}}</h3>
					<text>评分:{{item.score}}</text>
					<text>月销量:{{item.saleQuantity}}</text>
					<text>到店所需时间:{{item.deliveryTime}}</text>
					<text>到店距离:{{item.distance}}</text>
					<text>人均消费:{{item.avgCost}}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				shoplist:[],
				id:'',
				keyword:''
			}
		},
		methods: {
			search(index){
				uni.navigateTo({
					url:'search_food?keyword='+index
				})
			},
			todetails(id){
				uni.navigateTo({
					url:'shop_details?id='+this.shoplist[id].id
				})
			},
			
			getshoplist(){
				this.$u.get('/prod-api/api/takeout/seller/list?themeId='+this.id).then((res)=>{
					this.shoplist=res.rows
					console.log(res);
				})
			},
			// getshoplist_search(){
			// 	this.$u.get('/prod-api/api/takeout/search?keyword='+this.keyword).then(res=>{
			// 		this.shoplist=res.rows
			// 		console.log(res);
			// 	})
			// }
		},
		onLoad(options) {
			this.id=options.id
			this.keyword=options.keyword
			this.getshoplist()
			// this.getshoplist_search()
			// if(this.keyword==''){
			// 	this.getshoplist()
			// }else{
			// 	this.getshoplist_search()
			// }
		}
	}
</script>

<style scoped>
	.nearimg image{
		width: 230rpx;
		height: 230rpx;
		margin-right: 10rpx;
	}
	.nearlist{
		display: flex;
		flex-direction: row;
		margin: 10rpx;
		padding: 10rpx;
		box-shadow: 8rpx 8rpx 16rpx gray;
		border-radius: 20rpx;
		border: #A0CFFF 2rpx solid;
	}
	.neartext{
		display: flex;
		flex-direction: column;
	}
</style>
