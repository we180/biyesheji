<template>
	<view>
		<!-- 图文介绍，视频演示。 -->
		<view class="info">
			<u-image src="../../../../static/myimgs/myimg_zhizao/file_20220502cs24.jpg" width="100%" height="200rpx"></u-image>
			<h2 style="text-align: center;">中国商飞语音通信解决方案</h2>
			<h3 style="text-align: center;">中国商飞</h3>
			<text>中国商飞部署了几百台亿联SIP-T27P与SIP-T21P E2话机，用于各机构、各办事处之间的通讯交流，有效应对业务增长带来的各种沟通挑战， 同时又大大节约了通讯成本。</text>
			<video :src="'../../../../static/myimgs/myimg_zhizao/video02.mp4'" controls style="width: 100%;"></video>
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
			
		}
	}
</script>

<style scoped>
	.info{
		margin: 10rpx;
		padding: 10rpx;
		border: #ccc 2rpx solid;
		border-radius: 20rpx;
	}
</style>
