<template>
	<view>
		<!-- 封面、标题、副标题、详细内容、点赞数、“点赞”按钮，点击“点赞”按钮可以进行点赞。 -->
		<view class="newsinfo">
			<u-image width="100%" height="300rpx" :src="baseUrl+news.cover"></u-image>
			<h2 style="text-align: center;">{{news.title}}</h2>
			<h3>{{news.title}}</h3>
			<rich-text :nodes="news.content"></rich-text>
			<h3>点赞数:{{news.likeNum}}</h3>
			<u-button @click="dianzan" type="success">点赞</u-button>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				news:''
			}
		},
		methods: {
			dianzan(){
				this.$u.put('/prod-api/api/movie/press/press/like/'+this.id).then(res=>{
					console.log(res);
					this.getData()
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/movie/press/press/'+this.id)
				this.news=res1.data
				console.log(res1);
			}
		},
		onLoad(ops) {
			this.id=ops.id
			this.getData()
		}
	}
</script>

<style scoped>
	.newsinfo{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
