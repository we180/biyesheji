<template>
	<view>
		<view class="info">
			<u-row>
				<u-col span="4">
					<u-image width="100%" height="300rpx" :src="baseUrl+yingpian.cover"></u-image> 
				</u-col>
				<!-- 右侧上方显示影院名称，中间显示影院地址，下方显示影院评分 -->
				<u-col span="8">
					<view class="yingyuantext" style="display: flex;flex-direction: column;">
						<h3>{{yingpian.name}}</h3>
						<text>类型:{{yingpian.category}}</text>
						<text>上映时间:{{yingpian.playDate}}</text>
						<view class="" style="display: flex;flex-direction: row;margin-top: 20rpx;">
							<u-button @click="xiangkan" type="success">想看</u-button>
							<u-button @click="xiangkan" type="primary">看过</u-button>
						</view>
						
					</view>
				</u-col>
			</u-row>
			<u-gap></u-gap>
			<u-section title="影片简介" font-size="40" :right="false"></u-section>
			<view class="jianjie">
				<u-collapse>
					<u-collapse-item title="影片简介">
						<text>{{yingpian.introduction}}</text>
					</u-collapse-item>
				</u-collapse>
			</view>
			<view class="pingfen">
				<h3>影片评分:{{yingpian.score}}</h3>
				<h3>评论人数:{{comment_list.length}}</h3>
				<h3>想看:{{yingpian.likeNum}}</h3>
				<h3>看过:{{yingpian.favoriteNum}}</h3>
			</view>
			<u-gap></u-gap>
			<u-section title="写评论" font-size="40" :right="false"></u-section>
			<u-gap></u-gap>
			<u-button type="primary" @click="showpop=true">参与评论</u-button>
			<u-gap></u-gap>
			<view class="input">
				<u-popup mode="center" v-model="showpop">
					<u-input type="textarea" border="border" style="height: 200rpx;width: 500rpx;" v-model="comment"></u-input>
					<u-field label="评分" placeholder="0-5" v-model="score"></u-field>
					<u-button type="success" @click="submit">发表评论</u-button>
				</u-popup>
				
			</view>
			<u-gap></u-gap>
			<u-section title="评论列表" font-size="30" :right="false"></u-section>
			<view class="comment" v-for="(item,comment_listid) in comment_list" :key="comment_listid">
				<!-- 用户头像、用户名、打分（5个五角星标识分数）、评论内容、评论时间、点赞数 -->
				<text>用户名:{{item.nickName}}</text>
				<u-rate :current="item.score" :disabled="true"></u-rate>
				<text>评论内容:{{item.content}}</text>
				<text>评论时间:{{item.commentDate}}</text>
				<text>点赞数:{{item.likeNum}}</text>
			</view>
			<u-gap></u-gap>
			<u-gap></u-gap>
			<u-gap></u-gap>
			<u-gap></u-gap>
			<view class="goupiao">
				<u-button type="success" @click="goupiao">购票</u-button>
			</view>
		</view>
		<!-- 上方显示影片基本信息,中部显示影片简介，下方显示影片评论，底部显示“购票”按钮 -->
		<!-- 影片基本信息包括：左上方显示影片封面；右上方依次显示影片名称、类型、上映时间、“想看”和“看过”。 -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				score:'',
				showpop:false,
				id:'',
				yingpian:'',
				comment_list:[],
				comment:''
			}
		},
		methods: {
			xiangkan(){
				this.$u.toast('成功')
			},
			goupiao(){
				uni.navigateTo({
					url:'goupiao/goupiao?id='+this.id
				})
			},
			submit(){
				this.$u.post('/prod-api/api/movie/film/comment',{
					content:this.comment,
					movieId:this.id,
					score:this.score
				}).then(res=>{
					this.$u.toast('评论成功')
					this.getData()
					this.comment=''
					this.score=''
					setTimeout(()=>{
						this.showpop=false
					},700)
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/movie/film/detail/'+this.id)
				this.yingpian=res1.data
				console.log(this.yingpian.name);
				let res2=await this.$u.get('/prod-api/api/movie/film/comment/list?movieId='+this.id)
				this.comment_list=res2.rows
				console.log(res2);
			}
		},
		onLoad(ops) {
			this.id=ops.id
			this.getData()
		}
	}
</script>

<style scoped>
	.jianjie{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
	.goupiao{
		position: fixed;
		bottom: 10rpx;
		width: 100%;
		margin: 10rpx;
	}
	.comment{
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
