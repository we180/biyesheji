<template>
	<view>
		<view class="search">
			<u-search @custom="search" @search="search"></u-search>
		</view>
		<u-gap></u-gap>
		<view class="banner">
			<u-swiper :list="banner" :effect3d="true" @click="tobanner_De"></u-swiper> 
		</view>
		<u-gap></u-gap>
		<view class="type">
			<view class="typelist" v-for="(item,typelistid) in typelist.slice(0,9)" :key="typelistid" @click="clickicon(typelistid)">
				<u-icon :name="baseUrl+item.imgUrl" :label="item.serviceName" label-pos="bottom" size="80" label-size="24"></u-icon>
			</view>
			<view class="typelist" @click="toallservices">
				<u-icon name="more-dot-fill" label="更多服务" label-pos="bottom" size="80" label-size="24"></u-icon>
			</view>
		</view>
		<u-section title="热门主题" :right="false" font-size="33"></u-section>
		<u-gap></u-gap>
		<view class="hotpart">
			<view class="hotpartlist" v-for="(item,hotpartid) in hotpart" :key="hotpartid" @click="tohotpart_De(hotpartid)">
				<u-image :src="baseUrl+item.cover" width="100%" height="300rpx"></u-image>
				<h3 class="u-line-2">{{item.title}}</h3>
			</view>
		</view>
		<u-section title="新闻专栏" :right="false" font-size="33"></u-section>
		<view class="news">
			<u-tabs :list="newstype" :current="current" @change="changetab"></u-tabs>
			<view class="newslist" v-for="(item,newsid) in news" :key="newsid" @click="tonews_De(newsid)">
				<!-- 图片、新闻标题、新闻内容缩写（多出的字用省略号显示）、评论总数、发布时间等信息 -->
				<u-row>
					<u-col span="4">
						<u-image width="100%" height="230rpx" :src="baseUrl+item.cover"></u-image>
					</u-col>
					<u-col span="8">
						<h3 class="u-line-1">{{item.title}}</h3>
						<rich-text :nodes="item.content" class="u-line-4" style="height: 76px;"></rich-text>
						<view class="news_De">
							<text>评论总数:{{item.commentNum==null?'0':item.commentNum}}</text>
							<text>发布时间:{{item.publishDate}}</text>
						</view>
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
				banner:[],
				typelist:[],
				hotpart:[],
				newstype:[],
				current:0,
				news:[]
			}
		},
		methods: {
			clickicon(id){
				if(id==8){
					uni.navigateTo({
						url:"../allservices/car_park/car_park"
					})
				}else{
					console.log(id);
				}
			},
			search(index){
				uni.navigateTo({
					url:'../news/newslist?title='+index
				})
			},
			tobanner_De(id){
				uni.navigateTo({
					url:'../news/newsindex?id='+this.banner[id].targetId
				})
			},
			tohotpart_De(id){
				uni.navigateTo({
					url:'../news/newsindex?id='+this.hotpart[id].id
				})
			},
			tonews_De(id){
				uni.navigateTo({
					url:'../news/newsindex?id='+this.news[id].id
				})
			},
			toallservices(){
				uni.switchTab({
					url:'../allservices/allservices'
				})
			},
			changetab(index){
				this.current=index
				this.$u.get('/prod-api/press/press/list?type='+this.newstype[index].id).then(res=>{
					this.news=res.rows
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/rotation/list?type=2')
				// console.log(res1);
				this.banner=res1.rows.map(res=>{
					return{
						image:this.baseUrl+res.advImg,
						targetId:res.targetId
					}
				})
				let res2=await this.$u.get('/prod-api/api/service/list')
				// console.log(res2);
				this.typelist=res2.rows
				this.typelist.sort(function(a,b){
					return a.sort-b.sort
				})
				let res3=await this.$u.get('/prod-api/press/press/list?hot=Y')
				this.hotpart=res3.rows
				console.log(res3);
				let res4=await this.$u.get('/prod-api/press/category/list')
				this.newstype=res4.data
				// console.log(res4);
				let res5=await this.$u.get('/prod-api/press/press/list?type=9')
				this.news=res5.rows
				console.log(res5);
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
		flex-direction: row;
		flex-wrap: wrap;
	}
	.typelist{
		display: flex;
		width: 20%;
		justify-content: center;
		align-items: center;
		margin-bottom: 20rpx;
	}
	.hotpart{
		display: flex;
		flex-direction: row;
	}
	.hotpartlist{
		width: 100%;
		margin: 10rpx;
		padding:10rpx;
		border: #888 2rpx solid;
		border-radius: 20rpx;
	}
	.newslist{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: #888 2rpx solid;
	}
	.news_De{
		display: flex;
		justify-content: space-around;
		align-items: center;
		font-size: 27rpx;
	}
</style>
