<template>
	<!-- 标题、承办单位、提交时间和处理状态 -->
	<view>
		<view class="suqiulist">
			<view class="suqiu" v-for="(item,suqiulistid) in suqiulist" :key="suqiulistid" @click="tosuqiu_De(suqiulistid)">
				<h2>{{item.title}}</h2>
				<text>承办单位:{{item.undertaker}}</text>
				<text>提交时间:{{item.createTime}}</text>
				<text>处理状态:{{item.state==0?'未处理':'已处理'}}</text>
			</view>
		</view>
		<view class="fabu">
			<u-button type="success" @click="tofabu">发布诉求</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				suqiulist:[]
				
			}
		},
		methods: {
			tosuqiu_De(id){
				uni.navigateTo({
					url:'suqiu_details?id='+this.suqiulist[id].id
				})
			},
			tofabu(){
				uni.navigateTo({
					url:'xinjiansuqiu?id='+this.id
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/gov-service-hotline/appeal/list?appealCategoryId='+this.id)
				this.suqiulist=res1.rows
				console.log(res1);
			}
		},
		onShow() {
			this.getData()
		},
		onLoad(ops) {
			this.id=ops.id
			this.getData()
		},
	}
</script>

<style scoped>
	.suqiu{
		margin: 10rpx;
		padding: 10rpx;
		border: #ccc 2rpx solid;
		border-radius: 20rpx;
		display: flex;
		flex-direction: column;
	}
	.fabu{
		position: fixed;
		bottom: 0rpx;
		padding: 30rpx;
		width: 100%;
	}
</style>
