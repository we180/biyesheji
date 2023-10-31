<template>
	<!-- 搜索框、项目类型、公益类别、公益内容、发布人、已筹善款、项目时间、参捐人数
	下方显示“我要捐助”按钮，点击按钮即可捐款。公益列表底部显示分页，点击分页可以跳转列表页面 -->
	<view>
		<view class="search">
			<u-search @custom="search" @search="search"></u-search>
		</view>
		<view class="xiangmu_listall">
			<view class="xiangmu" v-for="(item,xiangmulistid) in xiangmulist" :key="xiangmulistid" @click="todetails(xiangmulistid)">
				<text>公益类别：{{item.type.name}}</text>
				<text>公益内容：{{item.name}}</text>
				<text>发布人：{{item.author}}</text>
				<text>已筹善款：{{item.moneyNow}}</text>
				<text>项目时间：{{item.createTime}}</text>
				<text>参捐人数：{{item.donateCount}}</text>
				<u-button type="success" @click="juan">我要捐助</u-button>
			</view>
		</view>
		<view class="juankuan">
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				xiangmulist:[]
			}
		},
		methods: {
			todetails(id){
				uni.navigateTo({
					url:'gonyi_details?id='+this.xiangmulist[id].id
					+'&img='+this.xiangmulist[id].imgUrl
					+'&name='+this.xiangmulist[id].name
					+'&moneyTotal='+this.xiangmulist[id].moneyTotal
					+'&donateCount='+this.xiangmulist[id].donateCount
					+'&createTime='+this.xiangmulist[id].createTime
				})
			},
			juan(){
				this.$u.toast('捐款成功')
			},
			search(index){
				this.$u.get('/prod-api/api/public-welfare/public-welfare-activity/list?name='+index).then((res)=>{
					this.xiangmulist=res.rows
					console.log(res);
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/public-welfare/public-welfare-activity/list?typeId='+this.id)
				this.xiangmulist=res1.rows
				console.log(res1);
			}
		},
		onLoad(options) {
			this.id=options.id
			this.getData()
		}
	}
</script>

<style scoped>
	.xiangmu{
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		box-shadow: 8rpx 8rpx 16rpx gray;
		border: #A0CFFF 2rpx solid;
	}
	.juankuan{
		width: 100%;
	}
</style>
