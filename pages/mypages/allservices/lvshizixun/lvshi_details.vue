<template>
	<view>
		<view class="top">
			<!-- 上部显示头像、名称、法律专长、咨询人数和服务次数 -->
			<u-row>
				<u-col span="4">
					<u-image width="100%" height="250rpx" :src="baseUrl+info.avatarUrl"></u-image> 
				</u-col>
				<u-col span="8" style="display: flex;flex-direction: column;" align="top">
					<text>{{info.name}}</text>
					<text>法律专长:{{info.legalExpertiseName}}</text>
					<text>咨询人数:{{info.serviceTimes}}</text>
					<text>服务次数:{{info.serviceTimes}}</text>
				</u-col>
			</u-row>
		</view>
		<view class="bottom">
			<!-- 下部显示两个tab页，分别是服务方式和用户评价， -->
			<u-tabs :list="list" :current="current" @change="changetabs" style="text-align: center;"></u-tabs>
			<view class="fuwu" v-if="current==0">
				<!-- 点击服务方式，展示律师基本信息、律师个人简介和律师证展示照片，律师基本信息包括教育背景、从业年限和执业证号 -->
				<u-image width="100%" height="300rpx" :src="baseUrl+info.certificateImgUrl.replace('/dev-api','/prod-api')"></u-image>
				<view class="fuwu_text">
					<h3 style="margin: 18rpx;">基本信息</h3>
					<text>教育背景:{{info.eduInfo}}</text>
					<text>从业年限:{{info.workStartAt}}</text>
					<text>执业证号:{{info.licenseNo}}</text>
					<h3 style="margin: 18rpx;">个人简介</h3>
					<text>{{info.baseInfo}}</text>
				</view>
			</view>
			<u-gap></u-gap>
			<u-gap></u-gap>
			<u-gap></u-gap>
			<view class="pingjia" v-if="current==1">
				<!-- 展示评价列表，内容包括用户头像、昵称、评价时间、评价内容、点赞按钮和点赞数量，点击点赞按钮切换点赞状态 -->
				<view class="pingjialist" v-for="(item,commentlistid) in commentlist" :key="commentlistid">
					<u-row>
						<u-col span="2">
							<u-avatar></u-avatar>
						</u-col>
						<u-col span="7" style="display: flex;flex-direction: column;" align="top">
							<text>昵称:{{item.fromUserName}}</text>
							<text>评价内容:{{item.evaluateContent}}</text>
						</u-col>
						<u-col span="3">
							<u-icon :name="item.myLikeState==true?'thumb-up-fill':'thumb-up'" color="#2979ff" size="60" @click="dianzan(commentlistid)"></u-icon><br>
							<text>点赞数量:{{item.likeCount}}</text>
						</u-col>
					</u-row>
					<text>评价时间:{{item.createTime}}</text>
				</view>
				
			</view>
			<u-button type="primary" @click="tofreezixun" class="zixun">免费咨询</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				current:0,
				id:'',
				info:'',
				list:[
					{
						name:'服务方式'
					},
					{
						name:'用户评价'
					}
				],
				commentlist:[]
			}
		},
		methods: {
			dianzan(id){
				if(this.commentlist[id].myLikeState==true){
					this.$u.post('/prod-api/api/lawyer-consultation/legal-advice/evaluate-like',{
						adviceId:this.commentlist[id].adviceId,
						like:false
					}).then(res=>{
						console.log(res);
						this.$u.toast('取消成功')
						this.getData()
					})
				}else{
					this.$u.post('/prod-api/api/lawyer-consultation/legal-advice/evaluate-like',{
						adviceId:this.commentlist[id].adviceId,
						like:true
					}).then(res=>{
						console.log(res);
						this.$u.toast('点赞成功')
						this.getData()
					})
				}
			},
			changetabs(index){
				this.current=index
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/lawyer-consultation/lawyer/'+this.id)
				this.info=res1.data
				console.log(res1);
				let res2=await this.$u.get('/prod-api/api/lawyer-consultation/lawyer/list-evaluate?lawyerId='+this.id)
				this.commentlist=res2.rows
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
	.fuwu_text{
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
	.zixun{
		position: fixed;
		bottom: 10rpx;
		width: 94%;
		margin-left: 3%;
	}
</style>
