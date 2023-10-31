<template>
	<view>
		<!-- 封面、标题、副标题、发布日期、点赞数， -->
		<view class="newslist" v-for="(item,newslistid) in newslist" :key="newslistid" @click="tonews_De(newslistid)">
			<u-image width="100%" height="300rpx" :src="baseUrl+item.cover"></u-image>
			<h2 style="text-align: center;">{{item.title}}</h2>
			<h3>{{item.title}}</h3>
			<text>发布日期:{{item.publishDate}}</text>
			<text>点赞数:{{item.likeNum}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				newslist:[]
			}
		},
		methods: {
			async getData(){
				let res1=await this.$u.get('/prod-api/api/movie/press/press/list')
				this.newslist=res1.rows
				console.log(res1);
			},
			tonews_De(id){
				uni.navigateTo({
					url:'xingwen_details?id='+this.newslist[id].id
				})
			},
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.newslist{
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
