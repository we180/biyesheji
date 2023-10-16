<template>
	<view>
		<view class="search">
			<u-search @custom="search" @search="search"></u-search>
		</view>
		<u-gap></u-gap>
		<view class="housetype">
			<u-icon name="home" color="#2979ff" size="88" label-pos="bottom" label="二手" label-size="40" @click="choosetype('二手')"></u-icon>
			<u-icon name="bookmark" color="#2979ff" size="88" label-pos="bottom" label="租房" label-size="40" @click="choosetype('租房')"></u-icon>
			<u-icon name="grid-fill" color="#2979ff" size="88" label-pos="bottom" label="楼盘" label-size="40" @click="choosetype('楼盘')"></u-icon>
			<u-icon name="man-add" color="#2979ff" size="88" label-pos="bottom" label="中介" label-size="40" @click="choosetype('中介')"></u-icon>
		</view>
		<u-gap></u-gap>
		<view class="house" v-for="(item,houselistid) in houselist" :key="houselistid" @click="tohouse_De(houselistid)">
			<!-- 图片、所在小区或商圈名称、房源面积以及价格、房源简介等内容 -->
			<u-image width="100%" height="350rpx" :src="baseUrl+item.pic"></u-image>
			<view class="housetext">
				<h3>{{item.address}}</h3>
				<text>房源面积:{{item.areaSize}}㎡</text>
				<text>价格:{{item.price}}</text>
				<text class="u-line-3">房源简介:{{item.description}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				houselist:[]
			}
		},
		methods: {
			search(index){
				this.$u.get('/prod-api/api/house/housing/list?sourceName='+index).then(res=>{
					this.houselist=res.rows
				})
			},
			choosetype(index){
				if(index=='二手'){
					this.$u.get('/prod-api/api/house/housing/list?houseType=二手').then(res=>{
						this.houselist=res.rows
						console.log(res);
					})
				}else if(index=='租房'){
					this.$u.get('/prod-api/api/house/housing/list?houseType=租房').then(res=>{
						this.houselist=res.rows
					})
				}else if(index=='楼盘'){
					this.$u.get('/prod-api/api/house/housing/list?houseType=楼盘').then(res=>{
						this.houselist=res.rows
					})
				}else if(index=='中介'){
					this.$u.get('/prod-api/api/house/housing/list?houseType=中介').then(res=>{
						this.houselist=res.rows
					})
				}
			},
			tohouse_De(id){
				uni.navigateTo({
					url:'house_details?id='+this.houselist[id].id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/house/housing/list')
				this.houselist=res1.rows
				console.log(res1);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.housetype{
		display: flex;
		justify-content: space-around;
	}
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
</style>
