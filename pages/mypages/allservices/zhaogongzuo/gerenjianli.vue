<template>
	<view>
		<view class="search">
			<u-search action-text="查询" @search="search" @custom="search"></u-search>
		</view>
		<u-gap></u-gap>
		<u-section title="基本信息" font-size="40" :right="false" v-if="searchflag"></u-section>
		<view class="info" v-if="searchflag">
			<!-- 用户昵称、邮件、电话号码、性别 -->
			<text>用户昵称:{{userinfo.nickName}}</text>
			<text>邮件:{{userinfo.email}}</text>
			<text>电话号码:{{userinfo.phonenumber}}</text>
			<text>性别:{{userinfo.sex=='0'?'男':'女'}}</text>
		</view>
		<u-section title="求职信息" font-size="40" :right="false"></u-section>
		<!-- 工作经验、最高学历、现居住地、期望职位、期望薪资、教育经历、个人简介 -->
		<view class="info">
			<text>工作经验:{{jianli.experience}}</text>
			<text>最高学历:{{jianli.mostEducation}}</text>
			<text>现居住地:{{jianli.address}}</text>
			<text>期望职位:{{jianli.positionId}}</text>
			<text>期望薪资:{{jianli.money}}</text>
			<text>教育经历:{{jianli.education}}</text>
			<text>个人简介:{{jianli.individualResume}}</text>
		</view>
		<view class="xiugai" style="padding: 10rpx;">
			<u-button type="success" @click="xiugai" v-if="searchflag">修改简历</u-button>
		</view>
		<view class="xinzeng">
			<u-button type="primary" @click="xinzeng">新增简历</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userinfo:'',
				jianli:'',
				searchflag:true
			}
		},
		methods: {
			search(index){
				this.$u.get('/prod-api/api/job/resume/queryResumeByUserId/'+index).then(res=>{
					this.jianli=res.data
					console.log(res);
					this.searchflag=false
				})
			},
			xiugai(){
				uni.navigateTo({
					url:'change_jianli?experience='+this.jianli.experience
					+'&mostEducation='+this.jianli.mostEducation
					+'&address='+this.jianli.address
					+'&positionId='+this.jianli.positionId
					+'&money='+this.jianli.money
					+'&education='+this.jianli.education
					+'&individualResume='+this.jianli.individualResume
					+'&state=0'
				})
			},
			xinzeng(){
				uni.navigateTo({
					url:'change_jianli?state=1'
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/common/user/getInfo')
				this.userinfo=res1.user
				console.log(res1);
				let res2=await this.$u.get('/prod-api/api/job/resume/queryResumeByUserId/'+this.userinfo.userId)
				this.jianli=res2.data
				console.log(res2);
				
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.info{
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
	.xinzeng{
		position: fixed;
		bottom: 14rpx;
		padding: 10rpx;
		width: 100%;
	}
</style>
