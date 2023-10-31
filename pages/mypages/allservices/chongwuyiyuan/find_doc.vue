<template>
	<!-- 页面显示医生列表，列表项左侧显示医生头像，右侧显示医生姓名、职称、执业编号、擅长描述和从业年限，点击列表项进入问诊页面 -->
	<view>
		<view class="doclistall">
			<view class="doclist" v-for="(item,doclistid) in doclist" :key="doclistid" @click="towenzhen(item)">
				<view class="docimg">
					<image :src="baseUrl+item.avatar" mode=""></image>
				</view>
				<view class="doctext">
					<h3>{{item.name}}</h3>
					<text>职称:{{item.jobName}}</text>
					<text>执业编号:{{item.practiceNo}}</text>
					<text>擅长描述:{{item.goodAt}}</text>
					<text>从业年限:{{item.workingYears}}年</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				doclist:[]
			}
		},
		methods: {
			towenzhen(item){
				uni.navigateTo({
					url:'wenzhen?item='+JSON.stringify(item)
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/pet-hospital/pet-doctor/list?typeId='+this.id)
				this.doclist=res1.rows
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
	.doctext{
		display: flex;
		flex-direction: column;
	}
	.docimg image{
		width: 220rpx;
		height: 220rpx;
	}
	.doclist{
		display: flex;
		flex-direction: row;
		margin: 10rpx;
		padding: 10rpx;
		border: #A0CFFF solid 2rpx;
		box-shadow: 8rpx 8rpx 16rpx gray;
		border-radius: 20rpx;
	}
</style>
