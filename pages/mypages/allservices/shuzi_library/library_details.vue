<template>
	<view class="page">
		<!-- 图书馆位置图片和图书馆信息。页面上方固定显示图书馆的位置图片，图片可缩放 -->
		<view class="img" style="margin-bottom: 300rpx;">
			<movable-area style="width: 100%;">
				<movable-view direction="all" scale="true" style="width: 100%;">
					<u-image width="100%" height="300rpx" :src="baseUrl+library.imgUrl"></u-image>
				</movable-view>
			</movable-area>
		</view>
		<!-- 图书馆名称、图书馆具体地址、图书馆介绍、营业时间、营业状态和评论按钮 -->
		<view class="info">
			<h3>{{library.name}}</h3>
			<text>图书馆具体地址:{{library.address}}</text>
			<text>图书馆介绍:{{library.description}}</text>
			<text>营业时间:{{library.businessHours}}</text>
			<text>营业状态:{{library.businessState=='1'?'营业中':'暂停营业'}}</text>
		</view>
		<view class="pinglun">
			<u-button type="success" @click="topinglun">评论</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				library:''
			}
		},
		methods: {
			topinglun(id){
				uni.navigateTo({
					url:'library_comment?id='+this.library.id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/digital-library/library/'+this.id)
				this.library=res1.data
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
	.info{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
		display: flex;
		flex-direction: column;
	}
</style>
