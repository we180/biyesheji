<template>
	<view>
		<view class="image">
			<h2 style="text-align: center;margin: 10rpx;" >大润发 12.12 "0元购"活动开启</h2>
			<u-image src="../../../../../static/myimgs/myimg_shequ/2.jpg" width="100%" height="360rpx"></u-image>
			<u-gap></u-gap>
			<u-section title="活动详情" :right="false" font-size="36"></u-section>
			<text>骊山新家园智慧社区一卡通系统会严格按照全国智标委归口的标准及文件要求组织建设与实施，进一步做好顶层设计、统一规划，结合后期运营需求，实现社区内的水、电、气、停车、小额消费医疗等功能，保证区域居民使用的一卡通能满足标准</text>
		</view>
		<view class="zixun" style="margin: 10rpx;">
			<u-section title="活动咨询" :right="false" font-size="36"></u-section>
			<u-gap></u-gap>
			<u-input type="textarea" v-model="content" border="border" style="margin: 10rpx;"></u-input>
			<u-button type="success" @click="tijiao">提交</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				content:''
			}
		},
		methods: {
			tijiao(){
				uni.navigateTo({
					url:'result'
				})
			},
		}
	}
</script>

<style scoped>
	.image{
		margin: 10rpx;
		padding: 10rpx;
		border: #A0CFFF 2rpx solid;
		border-radius: 20rpx;
	}
</style>
