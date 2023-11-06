<template>
	<view>
		<view class="huodonglist">
			<view class="huodong" @click="tohuodong_de">
				<u-image src="../../../../../static/myimgs/myimg_kaimo/597403047627b05a75c3dd.jpg" width="100%" height="220rpx"></u-image>
				<h2>金银花药材种植</h2>
				<h4>发起人:平顺县新的社会阶层人士联谊会</h4>
				<h4>活动简介:金银花药材种植项目</h4>
			</view>
			<view class="huodong" @click="tohuodong_de">
				<u-image src="../../../../../static/myimgs/myimg_kaimo/9.png" width="100%" height="220rpx"></u-image>
				<h2>助力早稻生产服务乡村振兴</h2>
				<h4>发起人:中共新田县委宣传部志愿服务队</h4>
				<h4>活动简介: 开展"助力早稻生产服务乡村振兴"活动</h4>
			</view>
			<view class="huodong" @click="tohuodong_de">
				<u-image src="../../../../../static/myimgs/myimg_kaimo/10.png" width="100%" height="220rpx"></u-image>
				<h2>“马路天使”志愿活动</h2>
				<h4>发起人:常德市西洞庭管理区农业农村局志愿服务队</h4>
				<h4>活动简介:“马路天使”志愿活动</h4>
			</view>
			<view class="huodong" @click="tohuodong_de">
				<u-image src="../../../../../static/myimgs/myimg_kaimo/11.png" width="100%" height="220rpx"></u-image>
				<h2>森林消防宣传</h2>
				<h4>发起人:常德市桃花源风景名胜区国有林场志愿者服务队</h4>
				<h4>活动简介:森林消防宣传</h4>
			</view>
			<view class="huodong" @click="tohuodong_de">
				<u-image src="../../../../../static/myimgs/myimg_kaimo/12.png" width="100%" height="220rpx"></u-image>
				<h2>优化营商环境 助力企业发展</h2>
				<h4>发起人:常德应急救援中心（常德市矿山救护队）</h4>
				<h4>活动简介:优化营商环境 助力企业发展</h4>
			</view>
		</view>
		<u-gap></u-gap>
		<u-gap></u-gap>
		<u-gap></u-gap>
		<u-gap></u-gap>
		<view class="huodongfaqi">
			<u-button type="primary" @click="tohuodongfaqi">活动发起</u-button>
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
			tohuodong_de(){
				uni.navigateTo({
					url:'huodong_de'
				})
			},
			tohuodongfaqi(){
				uni.navigateTo({
					url:'huodong_faqi'
				})
			},
		}
	}
</script>

<style scoped>
	.huodongfaqi{
		position: fixed;
		bottom: 24rpx;
		width: 100%;
		padding: 20rpx;
	}
	.huodong{
		margin: 10rpx;
		padding: 10rpx;
		display: flex;
		flex-direction: column;
		border: 2rpx solid #ccc;
		border-radius: 20rpx;
	}
</style>
