<template>
	<view>
		<view class="input">
			<u-input border="border" placeholder="请输入评论内容" v-model="comment" style="height: 200rpx;"></u-input>
			<u-button type="success" @click="submit" style="margin: 10rpx;">发表</u-button>
		</view>
		<u-gap></u-gap>
		<u-section title="评论列表" :right="false" font-size="40"></u-section>
		<view class="commentlist" v-for="(item,commentlistid) in commentlist" :key="commentlistid">
			<u-row>
				<u-col span="9">
					<h3>{{item.userName}}</h3>
					<text>{{item.content}}</text>
				</u-col>
				<u-col span="3">
					<u-icon :name="item.myLikeState==false?'thumb-up':'thumb-up-fill'" color="#2979ff" size="60" @click="dianzan(commentlistid)"></u-icon> 
				</u-col>
			</u-row>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				comment:'',
				commentlist:''
			}
		},
		methods: {
			dianzan(id){
				this.$u.post('/prod-api/api/digital-library/library-comment/like',{
					commentId:this.commentlist[id].id,
					like:true
				}).then(res=>{
					this.$u.toast('点赞成功')
					console.log(res);
					this.getData()
				})
			},
			submit(){
				this.$u.post('/prod-api/api/digital-library/library-comment',{
					libraryId:this.id,
					content:this.comment
				}).then(res=>{
					console.log(res);
					this.$u.toast('评论成功')
					this.comment=''
					this.getData()
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/digital-library/library-comment/list?libraryId='+this.id)
				this.commentlist=res1.data.sort((a,b)=>{
					return b.myLikeState-a.myLikeState
				})
				console.log(res1);
			},
		},
		onLoad(ops) {
			this.id=ops.id
			this.getData()
		}
	}
</script>

<style scoped>
	.commentlist{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
