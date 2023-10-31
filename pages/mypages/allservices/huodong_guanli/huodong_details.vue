<template>
	<view>
		<view class="huodonginfo">
			<u-image :src="baseUrl+huodong.imgUrl" width="100%" height="300rpx"></u-image>
			<h2 style="text-align: center;">{{huodong.name}}</h2>
			<rich-text :nodes="huodong.content"></rich-text>
		</view>
		<u-gap></u-gap>
		<u-section title="活动评论" font-size="40" :right="false"></u-section>
		<view class="comment">
			<u-input border="border" type="textarea" v-model="comment"></u-input>
			<u-button type="success" @click="submit">评论</u-button>
		</view>
		<u-gap></u-gap>
		<u-section :title="'查看评论 总计'+total+'条'" font-size="40" :right="false"></u-section>
		<view class="commentlist" v-for="(item,commentlistid) in commentlist" :key="commentlistid">
			<h3>用户:{{item.nickName}}</h3>
			<h4>{{item.content}}</h4>
			<h4>日期:{{item.commentTime}}</h4>
		</view>
		<u-gap></u-gap>
		<u-section title="活动推荐" font-size="40" :right="false"></u-section>
		<view class="commentlist" v-for="(item,recommendid) in recommend.slice(0,2)" :key="recommendid+999">
			<u-image width="100%" height="270rpx" :src="baseUrl+item.imgUrl"></u-image>
			<h3>{{item.name}}</h3>
		</view>
		<view class="baoming">
			<u-button type="success" @click="baoming">报名</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				huodong:'',
				comment:'',
				commentlist:'',
				total:'',
				recommend:[]
			}
		},
		methods: {
			baoming(){
				this.$u.toast('报名成功')
				setTimeout(()=>{
					uni.navigateBack({
						delta:1
					})
				},700)
			},
			submit(){
				this.$u.post('/prod-api/api/activity/comment',{
					activityId:this.id,
					content:this.comment
				}).then(res=>{
					console.log(res);
					this.comment=''
					this.$u.toast('评论成功')
					this.getcommentlist()
				})
				
			},
			getcommentlist(){
				this.$u.get('/prod-api/api/activity/comment/list?activityId='+this.id).then(res=>{
					this.commentlist=res.rows
					// console.log(res);
				})
				this.$u.get('/prod-api/api/activity/comment/number?activityId='+this.id).then(res=>{
					this.total=res.commentNum
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/activity/activity/'+this.id)
				this.huodong=res1.data
				// console.log(res1);
				let res3=await this.$u.get('/prod-api/api/activity/activity/list?recommend=Y')
				this.recommend=res3.rows
				console.log(res3);
			}
		},
		onLoad(ops) {
			this.id=ops.id
			this.getData()
			this.getcommentlist()
		}
	}
</script>

<style scoped>
	.huodonginfo{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
	.comment{
		margin: 10rpx;
		padding: 10rpx;
	}
	.commentlist{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
