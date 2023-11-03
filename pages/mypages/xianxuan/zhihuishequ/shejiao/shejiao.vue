<template>
	<view>
		<view class="head">
			<u-navbar title="友邻社交">
				<u-icon slot="right" name="edit-pen" style="margin-right: 20rpx;" size="60" label="发表图文" label-size="36" @click="tofabiao"></u-icon>
			</u-navbar>
		</view>
		<view class="tiebalist" @click="toshejiao_De">
			<view class="tiezi">
				<image src="../../../../../static/myimgs/myimg_shequ/1.jpg" mode=""></image>
				<h3 style="text-align: center;">维涅斯</h3>
			</view>
			<view class="tiezi">
				<image src="../../../../../static/myimgs/myimg_shequ/2.jpg" mode=""></image>
				<h3 style="text-align: center;">于里昂热</h3>
			</view>
		</view>
		<view class="tiebalist" @click="toshejiao_De">
			<view class="tiezi">
				<image src="../../../../../static/myimgs/myimg_shequ/3.jpg" mode=""></image>
				<h3 style="text-align: center;">生命威</h3>
			</view>
			<view class="tiezi">
				<image src="../../../../../static/myimgs/myimg_shequ/5.png" mode=""></image>
				<h3 style="text-align: center;">尤卢斯</h3>
			</view>
		</view>
		<view class="tiebalist" @click="toshejiao_De">
			<view class="tiezi">
				<image src="../../../../../static/myimgs/myimg_shequ/6.jpg" mode=""></image>
				<h3 style="text-align: center;">亚雷克</h3>
			</view>
			<view class="tiezi">
				<image src="../../../../../static/myimgs/myimg_shequ/u=1077953852,765179627&fm=26&fmt=auto&gp=0.jpg" mode=""></image>
				<h3 style="text-align: center;">马克西马</h3>
			</view>
		</view>
		<view class="tiebalist" @click="toshejiao_De">
			<view class="tiezi">
				<image src="../../../../../static/myimgs/myimg_shequ/u=1106075900,1685350778&fm=26&fmt=auto&gp=0.jpg" mode=""></image>
				<h3 style="text-align: center;">摩提夏</h3>
			</view>
			<view class="tiezi">
				<image src="../../../../../static/myimgs/myimg_shequ/u=2081009638,1317666904&fm=26&fmt=auto&gp=0.jpg" mode=""></image>
				<h3 style="text-align: center;">桑克瑞德</h3>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			toshejiao_De(){
				uni.navigateTo({
					url:'shejiao_de'
				})
			},
			tofabiao(){
				uni.navigateTo({
					url:'fabiao'
				})
			}
		}
	}
</script>

<style scoped>
	.tiebalist{
		display: flex;
		flex-direction: row;
	}
	.tiezi image{
		width: 100%;
	}
	.tiezi{
		width: 50%;
		margin: 10rpx;
		padding: 10rpx;
		border: #A0CFFF 2rpx solid;
		border-radius: 20rpx;
	}
</style>
