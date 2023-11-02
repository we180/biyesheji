<template>
	<view>
		<view class="info">
			<h2>2022深圳国际船艇及技术设备展览会</h2>
			<u-gap></u-gap>
			<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220502cs24.jpg" width="100%" height="230rpx"></u-image>
			<text>2022深圳国际船艇及其技术设备展览会（简称：GBIBS）将于2022年12月14-16日在深圳国际会展中心举办。中国（上海）国际船艇及其技术设备展览会（简称“CIBS”），携25年亚洲行业展会资源和对行业趋势的引领经验，将于2022年首次在深圳开展。</text>
			<u-gap></u-gap>
			<view class="video" v-if="state==1">
				<video :src="'../../../../../static/myimgs/myimg_zhizao/video02.mp4'" controls style="width: 100%;"></video>
			</view>
		</view>
		<view class="" v-if="state==0">
			<u-button type="success" @click="baoming">参展报名</u-button>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				state:0
			}
		},
		methods: {
			baoming(){
				uni.reLaunch({
					url:'result_baoming'
				})
			},
		},
		onLoad(ops) {
			this.state=ops.state
		},
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
