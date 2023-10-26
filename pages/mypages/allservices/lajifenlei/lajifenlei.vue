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
		<view class="daohang" style="display: flex;flex-direction: row;justify-content: space-around;margin-top: 20rpx;">
			<u-icon @click="sousuo" name="search" color="#2979ff" size="88" label="搜索" label-size="44" style="background-color: #A0CFFF;width: 40%;display: flex;flex-direction: row;justify-content: center;border-radius: 20rpx;"></u-icon>
			<u-icon @click="fenlei" name="grid" color="#2979ff" size="88" label="分类" label-size="44" style="background-color: #A0CFFF;width: 40%;display: flex;flex-direction: row;justify-content: center;border-radius: 20rpx;"></u-icon>
		</view>
		<u-gap></u-gap>
		<!-- <view class="type" style="display: flex;flex-direction: row;justify-content: space-around;">
			<u-icon name="integral" color="#2979ff" size="66" label="新时尚" label-size="33" label-pos="bottom"></u-icon>
			<u-icon name="thumb-up" color="#2979ff" size="66" label="党员在行动" label-size="33" label-pos="bottom"></u-icon>
			<u-icon name="man-add" color="#2979ff" size="66" label="分类达人" label-size="33" label-pos="bottom"></u-icon>
			<u-icon name="photo" color="#2979ff" size="66" label="社区动态" label-size="33" label-pos="bottom"></u-icon>
		</view> -->
		<u-tabs @change="changetab" :current="current" :list="newstype" style="text-align: center;"></u-tabs>
		<view class="news" v-for="(item,newslistid) in newslist" :key="newslistid" @click="tonews_de(newslistid)">
			<!-- 每条显示两行标题文字，多余采用缩略符。标题下面为日期时间。右侧为长方形新闻图片 -->
			<u-row>
				<u-col span="8">
					<h3 class="u-line-2">{{item.title}}</h3>
					<h4>日期时间:{{item.createTime}}</h4>
				</u-col>
				<u-col span="4">
					<u-image width="100%" height="220rpx" :src="baseUrl+item.imgUrl"></u-image> 
				</u-col>
			</u-row>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				current:0,
				banner:[],
				newstype:[],
				newslist:[]
			}
		},
		methods: {
			fenlei(){
				uni.navigateTo({
					url:'fenlei'
				})
			},
			tonews_de(id){
				uni.navigateTo({
					url:'news_details?id='+this.newslist[id].id
				})
			},
			changetab(index){
				this.current=index
				this.$u.get('/prod-api/api/garbage-classification/news/list?type='+this.newstype[index].id).then(res=>{
					this.newslist=res.rows
					console.log(res);
				})
			},
			sousuo(){
				uni.navigateTo({
					url:'sousuo'
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/garbage-classification/ad-banner/list')
				this.banner=res1.data
				console.log(res1);
				let res2=await this.$u.get('/prod-api/api/garbage-classification/news-type/list')
				this.newstype=res2.rows
				console.log(res2);
				let res3=await this.$u.get('/prod-api/api/garbage-classification/news/list?type=7')
				this.newslist=res3.rows
				console.log(res3);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.news{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
	}
</style>
