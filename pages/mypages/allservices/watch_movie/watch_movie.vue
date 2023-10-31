<template>
	<view>
		<view class="head" style="display: flex;flex-direction: row;">
			<u-icon name="map" color="#2979ff" size="60" label="南京" label-size="32"></u-icon>
			<view class="serach" @click="search" style="width: 80%;">
				<u-search></u-search>
			</view>
		</view>
		<u-gap></u-gap>
		<view class="banner">
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item v-for="(item,bannerid) in banner" :key="bannerid">
					<view class="swiper-item" @click="toyingpiande_b(bannerid)">
						<image :src="baseUrl+item.advImg" mode=""></image>
					</view>
				</swiper-item>
			</swiper>
		</view>
		<view class="tianqi">
			<!-- 天气、当前温度、湿度、空气质量 -->
			<u-notice-bar mode="horizontal" :list="tianqi"></u-notice-bar>
		</view>
		<view class="type" style="display: flex;justify-content: space-around;">
			<u-icon name="thumb-up" color="#2979ff" size="88" label-pos="bottom" label="推荐" label-size="34" @click="tuijian"></u-icon>
			<u-icon name="list" color="#2979ff" size="88" label-pos="bottom" label="预告" label-size="34" @click="yugao"></u-icon>
			<u-icon name="order" color="#2979ff" size="88" label-pos="bottom" label="影评" label-size="34" @click="toyingping"></u-icon>
			<u-icon name="grid" color="#2979ff" size="88" label-pos="bottom" label="星闻" label-size="34" @click="toxingwen"></u-icon>
		</view>
		<u-gap></u-gap>
		<u-section title="热映影片" font-size="40"></u-section>
		<u-gap></u-gap>
		<view class="reying">
			<scroll-view scroll-x="true">
				<view class="reyingall">
					<view class="reying_de" v-for="(item,reyingid) in reying.slice(0,3)" :key="reyingid">
						<image :src="baseUrl+item.cover" mode="" style="height: 300rpx;width:208rpx;" @click="toyingpian_De(reyingid)"></image>
						<h2 class="u-line-2" style="text-align: center;">{{item.name}}</h2>
						<u-button type="success" @click="goupiao(reyingid)">购票</u-button>
					</view>
				</view>
			</scroll-view>
		</view>
		<u-section title="即将上映影片" font-size="40"></u-section>
		<view class="reying">
			<scroll-view scroll-x="true">
				<view class="reyingall">
					<view class="reying_de" v-for="(item,reyingid) in reying.slice(10,13)" :key="reyingid">
						<image :src="baseUrl+item.cover" mode="" style="height: 300rpx;width:208rpx;" @click="toyingpian_De(reyingid+10)"></image>
						<h2 class="u-line-2" style="text-align: center;">{{item.name}}</h2>
						<u-button type="primary" @click="xiangkan">想看</u-button>
					</view>
				</view>
			</scroll-view>
		</view>
		<u-section title="周边影院" font-size="40"></u-section>
		<view class="yingyuan" v-for="(item,yingyuanid) in yingyuan" :key="yingyuanid">
			<u-row>
				<u-col span="4">
					<u-image width="100%" height="200rpx" :src="baseUrl+item.cover"></u-image> 
				</u-col>
				<!-- 右侧上方显示影院名称，中间显示影院地址，下方显示影院评分 -->
				<u-col span="8">
					<view class="yingyuantext" style="display: flex;flex-direction: column;">
						<h3>{{item.name}}</h3>
						<text>地址:{{item.address}}</text>
						<u-rate :current="5" :disabled="true"></u-rate> 
					</view>
				</u-col>
			</u-row>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				banner:[],
				tianqi:[
					'天气:多云  当前温度:10度  湿度:50% 空气质量:优'
				],
				reying:[],
				yingyuan:[],
			}
		},
		methods: {
			toxingwen(){
				uni.navigateTo({
					url:'xingwen/xingwen'
				})
			},
			toyingping(){
				uni.navigateTo({
					url:'yingping/yingping'
				})
			},
			yugao(){
				uni.navigateTo({
					url:'yugao/yugao'
				})
			},
			tuijian(){
				uni.navigateTo({
					url:'tuijianyingpian/tuijianyingpian'
				})
			},
			goupiao(id){
				uni.navigateTo({
					url:'goupiao/goupiao?id='+this.reying[id].id
				})
			},
			xiangkan(){
				this.$u.toast('收藏成功')
			},
			search(){
				uni.navigateTo({
					url:'search_yingpian'
				})
			},
			toyingpiande_b(id){
				uni.navigateTo({
					url:'yingpian_details?id='+this.banner[id].targetId
				})
			},
			toyingpian_De(id){
				uni.navigateTo({
					url:'yingpian_details?id='+this.reying[id].id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/movie/rotation/list')
				this.banner=res1.rows
				// console.log(res1);
				let res2=await this.$u.get('/prod-api/api/movie/film/list?recommend=Y')
				this.reying=res2.rows
				console.log(res2);
				let res3=await this.$u.get('/prod-api/api/movie/theatre/list')
				this.yingyuan=res3.rows
				// console.log(res3);
			},
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.reyingall{
		display: flex;
		flex-direction: row;
	}
	.reying_de{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
	.yingyuan{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
	.swiper-item image{
		width: 100%;
	}
</style>
