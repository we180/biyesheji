<template>
	<view>
		<!-- 村名称，村情况介绍，村环境照片展示，发布时间，发布人，查看数量， -->
		<h2 style="text-align: center;">秦峰镇新塘村</h2>
		<u-gap></u-gap>
		<h3 style="text-align: center;">尾道仁涯町政府</h3>
		<h3 style="text-align: center;">2022/12/10</h3>
		<u-image src="../../../../../static/myimgs/myimg_fupin/8abe3f56303248033f031f01f7522700@2x.png" width="100%" height="200rpx" border-radius="20rpx"></u-image>
		<view class="text">
			<text>
				近日，秦峰镇新塘村村民委员会为感谢锁进先生为秦峰镇新塘村的扶贫事业做出的杰出贡献，特聘锁进先生为新塘村的“名誉村主任”。锁进先生是江西渝网科技股份有限公司董事长，上饶开阳即渝网旗下全资子公司，此前一直专注于扶贫事业，经商的同时不忘回馈社会，积极履行应尽的社会责任，呼吁更多社会人士共同营造互相关心、互相帮助、互相支持的良好社会氛围。
				当下，推进精准扶贫，加大帮扶力度，是缓解贫困、实现共同富裕的内在要求，也是实现全面小康和现代化建设的一场攻坚战。扶贫在于精准，捐款只是其中一种，技术一样改变生活。现在正有越来越多的科技企业正在加入社会扶贫的大部队，也有不少科技促进产业发展的例子。目前很多偏僻地区，村中的青壮年常年外出务工，只剩下劳动力较弱的老年人。这时候以科学技术带动产业发展就至关重要了。不少科技企业起到良好的表率作用，紧紧结合产业实际情况，拓展新思路，以温情扶贫扶智，切实发挥科技助力产业发展的积极作用。密切结合乡政府制定的产业发展路子，走出一条适合老百姓发展的产业致富之路。　
			</text>
			<h3>查看数量:114514</h3>
		</view>
		<view class="fuping" style="padding: 10rpx;">
			<u-button type="success" @click="towoyaofuping">我要扶贫</u-button>
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
			towoyaofuping(){
				uni.navigateTo({
					url:'woyaofuping'
				})
			},
		}
	}
</script>

<style scoped>
	.text{
		margin: 10rpx;
		padding: 10rpx;
		border: #ccc 2rpx solid;
		border-radius: 20rpx;
	}
</style>
