<template>
	<view>
		<!-- 显示店家列表以及店内的对应菜品，菜品信息包括图片、菜名和价格，点击进入对应详情页面。 -->
		<view class="near">
			<view class="nearlist" v-for="(item,shoplist) in shoplist" :key="shoplist" @click="todetails(shoplist)">
				<view class="nearimg">
					<image :src="baseUrl+item.productList[0].imgUrl" mode=""></image>
				</view>
				<view class="neartext">
					<h3>{{item.name}}</h3>
					<h3>菜名:{{item.productList[0].name}}</h3>
					<h3>价格:{{item.productList[0].price}}</h3>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				keyword:'',
				shoplist:[]
			}
		},
		methods: {
			todetails(id){
				uni.navigateTo({
					url:'shop_details?id='+this.shoplist[id].productList[0].sellerId
				})
			},
			getlist_search(){
				this.$u.get('/prod-api/api/takeout/search?keyword='+this.keyword).then(res=>{
					this.shoplist=res.rows
					console.log(res);
				})
			}
		},
		onLoad(ops) {
			this.keyword=ops.keyword
			this.getlist_search()
		}
	}
</script>

<style scoped>
	.nearimg image {
		width: 230rpx;
		height: 230rpx;
		margin-right: 10rpx;
	}

	.nearlist {
		display: flex;
		flex-direction: row;
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: #A0CFFF 2rpx solid;
	}

	.neartext {
		display: flex;
		flex-direction: column;
	}
</style>
