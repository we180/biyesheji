<template>
	<view>
		<u-gap></u-gap>
		<view class="">
			<u-button type="primary" @click="toyouhaojisuan">油耗计算</u-button>
		</view>
		<u-gap></u-gap>
		<u-section title="资讯动态" font-size="40" :right="false"></u-section>
		<u-gap></u-gap>
		<view class="news">
			<!-- 封面、标题、发布时间、阅读数，每行显示“点赞”按钮，点击用户可以点赞 -->
			<view class="newslist" v-for="(item,newslistid) in newslist" :key="newslistid" @click="tonews_de(newslistid)">
				<u-row>
					<u-col span="3">
						<u-image width="100%" height="220rpx" :src="baseUrl+item.cover"></u-image> 
					</u-col>
					<u-col span="7">
						<h3 class="u-line-2">{{item.title}}</h3>
						<u-gap></u-gap>
						<h4>发布时间:{{item.publishDate}}</h4>
						<h4>阅读数:{{item.readNum}}</h4>
					</u-col>
					<u-col span="2">
						<u-button type="success" @click="dianzan">点赞</u-button>
					</u-col>
				</u-row>
			</view>
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
			toyouhaojisuan(){
				uni.navigateTo({
					url:'youhaojisuan'
				})
			},
			tonews_de(id){
				uni.navigateTo({
					url:'news_details?id='+this.newslist[id].id
				})
			},
			dianzan(){
				this.$u.toast('点赞成功')
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/park/press/press/list')
				this.newslist=res1.rows
				console.log(res1);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.newslist{
		padding: 10rpx;
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
		margin: 10rpx;
	}
</style>
