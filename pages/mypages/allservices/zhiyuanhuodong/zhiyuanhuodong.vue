<template>
	<view>
		<view class="banner">
			<u-swiper :list="banner" :effect3d="true"></u-swiper>
		</view>
		<u-gap></u-gap>
		<!-- 图片、新闻片段、发布时间，优先顶部显示最新发布的新闻 -->
		<view class="news" v-for="(item,newslistid) in newslist" :key="newslistid">
			<u-image width="100%" height="300rpx" :src="baseUrl+item.imgUrl"></u-image>
			<text>{{item.summary}}</text>
			<text>发布时间:{{item.createTime}}</text>
		</view>
		<view class="buttom">
			<u-icon name="bookmark" color="#2979ff" label="志愿活动" size="70" label-pos="bottom" label-size="38" @click="tozhiyuanindex"></u-icon>
			<u-icon name="account" color="#2979ff" label="我的活动" size="70" label-pos="bottom" label-size="38" @click="tomy_huodong"></u-icon>
		</view>
		<u-gap></u-gap>
		<u-gap></u-gap>
		<u-gap></u-gap>
		<u-gap></u-gap>
		<u-gap></u-gap>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				banner: [],
				newslist: []
			}
		},
		methods: {
			tozhiyuanindex(){
				uni.navigateTo({
					url:'zhiyuanhuodong_index'
				})
			},
			tomy_huodong(){
				uni.navigateTo({
					url:'my_huodong'
				})
			},
			async getData() {
				let res1 = await this.$u.get('/prod-api/api/volunteer-service/ad-banner/list')
				this.banner = res1.data.map((res) => {
					return {
						image: this.baseUrl + res.imgUrl
					}
				})
				let res2 = await this.$u.get('/prod-api/api/volunteer-service/news/list')
				this.newslist = res2.rows
				console.log(res2);
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
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
		display: flex;
		flex-direction: column;
	}
	.buttom{
		position: fixed;
		width: 90%;
		bottom: 120rpx;
		right: 5%;
		display: flex;
		justify-content: space-around;
	}
	.buttom>*{
		background-color: #FAB6B6;
		padding: 12rpx;
		border-radius: 20rpx;
	}
</style>
