<template>
	<view>
		<view class="search">
			<u-search @custom="search" @search="search"></u-search>
		</view>
		<view class="info" v-if="state==1">
<!-- 物流公司logo、名称和投诉电话图标，下部显示物流派送过程信息步进时间线，信息包括时间、地点和跟踪进度，底部显示物流投诉按钮。 -->
			<u-image width="100%" height="300rpx" :src="baseUrl+yundan.company.imgUrl"></u-image>
			<h3 style="text-align: center;">{{yundan.company.name}}</h3>
			<u-icon name="phone" color="#2979ff" size="66" :label="'投诉电话:'+yundan.company.phone" label-size="33"></u-icon>
			<view class="bujin" v-for="(item,yundanid) in yundan.stepList" :key="yundanid">
				<text>时间:{{item.eventAt}}</text>
				<text>地点:{{item.addressAt}}</text>
				<text>跟踪进度:{{item.stateName}}</text>
			</view>
			<view class="tousu">
				<u-button type="error" @click="tousu">投诉</u-button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				yundan:'',
				state:0
			}
		},
		methods: {
			search(index){
				this.$u.get('/prod-api/api/logistics-inquiry/logistics_info/'+index).then(res=>{
					this.yundan=res.data
					console.log(res);
					this.state=1
					
				})
			},
			tousu(){
				uni.navigateTo({
					url:'tousu_list'
				})
			},
		},
		onLoad() {
			
		}
	}
</script>

<style scoped>
	.bujin{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
		display: flex;
		flex-direction: column;
	}
</style>
