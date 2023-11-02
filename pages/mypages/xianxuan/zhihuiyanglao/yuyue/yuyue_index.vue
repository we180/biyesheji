<template>
	<view>
		<view class="head">
			<view class="image">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_yanglao/u=259881674,1275827384&fm=26&fmt=auto&gp=0.jpg"
							width="100%" height="180rpx" border-radius="20rpx"></u-image>
					</u-col>
					<u-col span="8">
						<view class="text">
							<h3>泰成逸园医养结合养老院</h3>
							<u-rate :count="5" :current="4.7" :disabled="true"></u-rate>
							<br>
							<u-icon name="map" label="广岛新日暮里114号" color="#2979ff"></u-icon>
						</view>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
		</view>
		<view class="info">
			<h2>养老机构简介</h2>
			<text>泰成逸园秉承“医养结合，持续照料”的理念，由长者养护中心、国际福祉用品（检测）展示中心三个核心板块构成，同时从长者“身、心、灵”的全方位需求出发，高标准倾力打造了完善的适老化硬件配套体系以及智能化平台支持下的“三大天使”照护服务体系，能让不同需求的长者均获得贴心的城中养老照护服务，泰成逸园养老院2017年9月7日广东省民政厅正式批准设立，养老机构设立许可证编号为：广东省民政厅颁发的省级养老院许可证，党和政府在中国人口老龄化日益严峻的今天，一直高度重视新时期新式医养结合养老院的建设泰成逸园一如既往地奋勇前进，打造中国养老行业新标杆！欢迎国内外长者前来参观。</text>
		</view>
		<u-gap style="background-color: #eeeddd;"></u-gap>
		<view class="info">
			<h3>服务对象</h3>
			<text>60岁以上老人</text>
			<h3>基础配套的设施设备</h3>
			<text>老人房间设施:护理床、呼叫器、储物柜、床头灯、电视、空调、冰箱、电话、独立卫生间、热水器、洗衣机、阳台、采暖、新风系统、智能马桶
			</text>
			<h3>服务体系:</h3>
			<h4>养护中心</h4>
			<h4>生活娱乐</h4>
			<h4>介护中心</h4>
			<h3>服务体系:</h3>
			<text>半年(随时可续签)</text>
		</view>
		<view class="">
			<u-button type="primary" @click="yuyue">立即预约</u-button>
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
			yuyue(){
				this.$u.toast('预约成功')
			}
		}
	}
</script>

<style scoped>
	.text>* {
		margin: 10rpx;
	}

	.info {
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: #A0CFFF 2rpx solid;
	}
</style>
