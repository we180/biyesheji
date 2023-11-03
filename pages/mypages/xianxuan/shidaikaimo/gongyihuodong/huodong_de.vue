<template>
	<view>
		<view class="info">
			<u-image src="../../../../../static/myimgs/myimg_kaimo/597403047627b05a75c3dd.jpg" width="100%" height="220rpx"></u-image>
			<text>平顺县全面推进乡村振兴，加快农业农村现代化，是需要全党高度重视的一个关系大局的重大问题。要加快发展乡村产业，顺应产业发展规律，立足当地特色资源，推动乡村产业发展壮大，优化产业布局，完善利益联结机制，让农民更多分享产业增值收益。2018年10月23日，习近平在广东考察时强调 ：“产业扶贫是最直接、最有效的办法，也是增强贫困地区造血功能、帮助群众就地就业的长远之计。要加强产业扶贫项目规划，引导和推动更多产业项目落户贫困地区。”</text>
			<video src="../../../../../static/myimgs/myimg_kaimo/video03.mp4" controls style="width: 100%;"></video>
			<u-button type="success" @click="baoming">活动报名</u-button>
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
			baoming(){
				this.$u.toast('报名成功')
			},
		}
	}
</script>

<style scoped>
	.info{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #ccc;
		border-radius: 20rpx;
	}
</style>
