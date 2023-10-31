<template>
	<view>
		<view class="head">
			<u-icon name="map" size="60" @click="tomapindex" :label="address"></u-icon>
			<view class="search">
				<u-search @custom="search" @search="search"></u-search>
			</view>
			
		</view>
		<u-gap></u-gap>
		<view class="banner">
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item v-for="(item,banner) in banner" :key="banner">
					<view class="swiper-item">
						<image :src="baseUrl+item.advImg" mode=""></image>
					</view>
				</swiper-item>
			</swiper>
		</view>
		<view class="typelist">
			<view class="type" v-for="(item,type) in type" :key="type" @click="tolist(type)">
				<u-icon :name="baseUrl+item.imgUrl" :label="item.themeName" size="60" label-pos="bottom"></u-icon>
			</view>
		</view>
		<u-gap></u-gap>
		<u-section :right="false" font-size="40" title="推荐好店"></u-section>
		<view class="recommend">
<!-- 3 行显示，一行里面显示 2 家店家信息，每个店家入口布局为上方显示店家封面，封面下为店家名称、评分及近 3 小时下单数 -->
			<view class="re_list" v-for="(item,recommend) in recommend" :key="recommend" @click="todetails(recommend)">
				<image :src="baseUrl+item.imgUrl" mode=""></image>
				<h3>{{item.name}}</h3>
				<text>评分:{{item.score}}</text>
				<text>近3小时下单数:{{item.saleNum3hour}}</text>
			</view>
		</view>
<!-- 左侧店家封面，右侧上方显示店家名称、评分（最多 5 分）、月销量、到店所需时间、到店距离、人均消费 -->
		<u-section :right="false" font-size="40" title="附近店家"></u-section>
		
		<view class="near">
			<view class="nearlist" v-for="(item,near) in near" :key="near" @click="todetails2(near)">
				<view class="nearimg">
					<image :src="baseUrl+item.imgUrl" mode=""></image>
				</view>
				<view class="neartext">
					<h3>{{item.name}}</h3>
					<text>评分:{{item.name}}</text>
					<text>月销量:{{item.saleQuantity}}</text>
					<text>到店所需时间:{{item.deliveryTime}}</text>
					<text>到店距离:{{item.distance}}</text>
					<text>人均消费:{{item.avgCost}}</text>
				</view>
			</view>
		</view>
		<u-gap></u-gap>
		<u-gap></u-gap>
		<u-gap></u-gap>
		<u-gap></u-gap>
		<u-gap></u-gap>
		<view class="tabs">
			<view class="tabitem">
				<u-icon name="home" label="首页" size="50" label-pos="bottom" label-size="30"></u-icon>
				<u-icon name="order" label="订单" size="50" label-pos="bottom" label-size="30" @click="toorder"></u-icon>
				<u-icon name="account" label="我的" size="50" label-pos="bottom" label-size="30" @click="tomyinfo"></u-icon>
			</view>
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				address:'',
				banner:[],
				type:[],
				recommend:[],
				near:[]
			}
		},
		methods: {
			todetails(id){
				uni.navigateTo({
					url:'shop_details?id='+this.recommend[id].id
				})
			},
			todetails2(id){
				uni.navigateTo({
					url:'shop_details?id='+this.near[id].id
				})
			},
			search(index){
				uni.navigateTo({
					url:'search_food?keyword='+index
				})
			},
			toorder(){
				uni.navigateTo({
					url:'orderlist'
				})
			},
			tomyinfo(){
				uni.navigateTo({
					url:'myinfo'
				})
			},
			tolist(id){
				uni.navigateTo({
					url:'shoplist?id='+this.type[id].id
				})
			},
			tomapindex(){
				uni.navigateTo({
					url:'map_index'
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/takeout/rotation/list')
				this.banner=res1.rows
				// console.log(res1);
				let res2=await this.$u.get('/prod-api/api/takeout/theme/list')
				this.type=res2.data
				// console.log(res2);
				let res3=await this.$u.get('/prod-api/api/takeout/seller/list?recommend=Y')
				this.recommend=res3.rows
				console.log(res3);
				let res4=await this.$u.get('/prod-api/api/takeout/seller/near')
				this.near=res4.rows
				console.log(res4);
				
			}
		},
		onShow() {
			if(this.address==null||this.address==''){
				this.address='新日暮里'
			}else{
				this.address=uni.getStorageSync('address')
			}
			
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.head{
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}
	.search{
		width: 70%;
	}
	.swiper-item image{
		width: 100%;
	}
	.typelist{
		margin-top: 10rpx;
		display: flex;
		flex-direction: row;
	}
	.type{
		width: 20%;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.recommend{
		margin-top: 10rpx;
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
	}
	.re_list{
		width: 46%;
		display: flex;
		flex-direction: column;
		margin-top: 20rpx;
	}
	.re_list image{
		width: 100%;
		height: 200rpx;
	}
	.recommend>*{
		margin: 2%;
		padding: 10rpx;
		box-shadow: 8rpx 8rpx 16rpx gray;
		border-radius: 20rpx;
		border: #A0CFFF 2rpx solid;
	}
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
	.tabitem{
		width: 100vw;
		display: flex;
		justify-content: space-around;
	}
	.tabitem>*{
		background-color: #A0CFFF;
		width: 20%;
		margin: 10rpx;
		padding: 10rpx;
		box-shadow: 8rpx 8rpx 16rpx gray;
		border-radius: 20rpx;
		border: #A0CFFF 2rpx solid;
	}
	.tabs{
		position: fixed;
		bottom: 120rpx;
	}
</style>
