<template>
	<view>
		<view class="banner">
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item v-for="(item,bannerid) in banner" :key="bannerid">
					<view class="swiper-item">
						<image :src="baseUrl+item.imgUrl" mode="" style="width: 100%;"></image>
					</view>
				</swiper-item>
			</swiper>
		</view>
		<u-gap></u-gap>
		<view class="search">
			<u-search @custom="search" @search="search"></u-search>
		</view>
		<u-gap></u-gap>
		<u-section title="热门搜索" font-size="40" :right="false"></u-section>
		<u-gap></u-gap>
		<view class="remenall">
			<view class="remen" v-for="(item,hotid) in hot" :key="hotid">
				<h3>{{item.keyword}}</h3>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				banner:[],
				hot:[]
			}
		},
		methods: {
			search(){
				
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/garbage-classification/poster/list')
				this.banner=res1.data
				console.log(res1);
				let res2=await this.$u.get('/prod-api/api/garbage-classification/garbage-classification/hot/list')
				this.hot=res2.data
				console.log(res2);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.remen{
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
		width: 33.333%;
		height: 100rpx;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.remenall{
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
	}
</style>
