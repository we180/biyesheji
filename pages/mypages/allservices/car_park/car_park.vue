<template>
	<view>
		<view class="banner">
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item v-for="(item,bannerid) in banner" :key="bannerid">
					<view class="swiper-item">
						<image :src="baseUrl+item.advImg" mode="" style="width: 100%;"></image>
					</view>
				</swiper-item>
			</swiper>
		</view>
		<u-gap></u-gap>
		<view class="type">
			<u-icon @click="totongchechang" name="home" color="#2979ff" size="66" label="停车场" label-size="33" label-pos="bottom"></u-icon>
			<u-icon @click="tozhaochewei" name="coupon" color="#2979ff" size="66" label="找车位" label-size="33" label-pos="bottom"></u-icon>
			<u-icon @click="tochangneizhaoche" name="man-add" color="#2979ff" size="66" label="场内找车" label-size="33" label-pos="bottom"></u-icon>
			<u-icon @click="tonuoche" name="car" color="#2979ff" size="66" label="挪车" label-size="33" label-pos="bottom"></u-icon>
			<u-icon @click="tocheshenghuo" name="bag" color="#2979ff" size="66" label="车生活" label-size="33" label-pos="bottom"></u-icon>
		</view>
		<u-gap></u-gap>
		<u-section title="新闻资讯" font-size="40" :right="false"></u-section>
		<view class="newslist" :class="newslistid%2==0?'news_ou':'news_ji'" v-for="(item,newslistid) in newslist" :key="newslistid" @click="tonews_De(newslistid)">
			<view class="newsimg">
				<u-image width="100%" height="300rpx" :src="baseUrl+item.cover"></u-image>
			</view>
			<view class="newstext">
				<!-- 新闻标题、新闻内容、评论总数、发布时间 -->
				<h3 class="u-line-2">{{item.title}}</h3>
				<rich-text :nodes="item.content" class="u-line-3"></rich-text>
				<view class="" style="display: flex;flex-direction: row;justify-content: space-around;">
					<text>评论总数:{{item.commentNum}}</text>
					<text>发布时间:{{item.publishDate}}</text>
				</view>
				
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				banner:[],
				newslist:[]
			}
		},
		methods: {
			tonews_De(id){
				uni.navigateTo({
					url:'cheshenghuo/news_details?id='+this.newslist[id].id
				})
			},
			tocheshenghuo(){
				uni.navigateTo({
					url:'cheshenghuo/cheshenghuo'
				})
			},
			tonuoche(){
				uni.navigateTo({
					url:'nuoche/nuoche'
				})
			},
			tochangneizhaoche(){
				uni.navigateTo({
					url:'changneizhaoche/changneizhaoche'
				})
			},
			totongchechang(){
				uni.navigateTo({
					url:'tingchechang/tingchechang'
				})
			},
			tozhaochewei(){
				uni.navigateTo({
					url:'zhaochewei/zhaochewei'
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/park/rotation/list')
				this.banner=res1.rows
				console.log(res1);
				let res2=await this.$u.get('/prod-api/api/park/press/press/list')
				this.newslist=res2.rows
				console.log(res2);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.type{
		display: flex;
	}
	.type>*{
		width: 20%;
	}
	.news_ji{
		padding: 10rpx;
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
		margin: 10rpx;
	}
	.news_ou{
		display: flex;
		flex-direction: row;
		border: 2rpx solid #aaa;
		margin: 10rpx;
		border-radius: 20rpx;
	}
	.news_ou>*{
		width: 50%;
		padding: 10rpx;
	}
</style>
