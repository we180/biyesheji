<template>
	<view>
		<view class="banner" >
			<u-swiper :list="banner" :effect3d="true" @click="todetails_banner"></u-swiper>
		</view>
		<view class="news">
			<u-tabs :list="news_type" :current="current" @change="changetype"></u-tabs>
			<view class="newslist" v-for="(item,newslistid) in newslist" :key="newslistid" @click="todetails(newslistid)">
				<view class="newsimg">
					<image :src="baseUrl+item.cover" mode="aspectFill"></image>
				</view>
				<view class="newstext">
					<span class="u-line-2">{{item.title}}</span>
					<rich-text :nodes="item.content" class="u-line-3"></rich-text>
					<view class="newsindex">
						<span>阅读总数:{{item.readNum==null?'0':item.readNum}}</span>
						<span>点赞数:{{item.likeNum}}</span>
					</view>
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
				news_type:[],
				newslist:[],
				current:0
			}
		},
		methods: {
			todetails(id){
				uni.navigateTo({
					url:'newsindex?id='+this.newslist[id].id
				})
			},
			todetails_banner(id){
				uni.navigateTo({
					url:'/pages/mypages/news/newsindex?id='+this.banner[id].targetId
				})
			},
			changetype(index) {
				this.current = index
				this.$u.get('/prod-api/press/press/list?type=' + this.news_type[index].id).then((res) => {
					this.newslist = res.rows
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/rotation/list?type=2')
				this.banner=res1.rows.map((res)=>{
					return{
						image:this.baseUrl+res.advImg,
						targetId:res.targetId
					}
				})
				console.log(res1);
				let res2 = await this.$u.get('/prod-api/press/category/list')
				this.news_type = res2.data
				let res5 = await this.$u.get('/prod-api/press/press/list?type=9')
				this.newslist = res5.rows
				console.log(res5);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.newslist {
		display: flex;
		flex-direction: row;
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: solid 4rpx pink;
		box-shadow: 8rpx 8rpx 16rpx skyblue;
		background-color: aliceblue;
	}
	
	.newsimg image {
		width: 230rpx;
		height: 230rpx;
	}
	
	.newsindex {
		display: flex;
		justify-content: space-between;
		font-size: 26rpx;
	}
	.newstext{
		height: 230rpx;
		width: 235px;
		overflow: hidden;
	}
</style>
