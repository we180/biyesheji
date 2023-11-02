<template>
	<view>
		<view class="banner">
			<u-swiper :list="banner" :effect3d="true"></u-swiper>
		</view>
		<u-gap></u-gap>
		<view class="type">
			<u-icon name="list" label="厂商列表" size="100" label-pos="bottom" @click="tochangshanglist"></u-icon>
			<u-icon name="order" label="产品列表" size="100" label-pos="bottom" @click="tochanpinlist"></u-icon>
			<u-icon name="file-text" label="展会活动" size="100" label-pos="bottom" @click="tozhanhuihuodong"></u-icon>
			<u-icon name="man-add" label="厂商招聘" size="100" label-pos="bottom" @click="tozhaopin"></u-icon>
			<u-icon name="home" label="厂商入驻" size="100" label-pos="bottom" @click="toruzhu"></u-icon>
		</view>
		<u-gap></u-gap>
		<u-section title="推荐厂商" :right="false" font-size="40"></u-section>
		<view class="recommend_changshang" @click="tochangshang_de">
			<!-- 文字介绍,视频宣传片 -->
			<view class="changshang_re">
				<u-image src="../../../../static/myimgs/myimg_zhizao/file_20220502cs09.jpg" width="100%" height="200rpx"></u-image>
				<h2>华为</h2>
				<text class="u-line-3">华为消费者业务产品全面覆盖手机、移动宽带终端、终端云等，凭借自身的全球化网络优势、全球化运营能力，致力于将最新的科技带给消费者，让世界各地享受到技术进步的喜悦，以行践言，实现梦想。</text>
			</view>
			<view class="changshang_re">
				<u-image src="../../../../static/myimgs/myimg_zhizao/file_20220502cs06.jpg" width="100%" height="200rpx"></u-image>
				<h2>中芯国际</h2>
				<text class="u-line-3">中芯国际是一家纯晶圆代工厂，向全球客户提供0.35微米到14纳米8寸和12寸芯片代工与技术服务。中芯国际除高端的制造能力之外，还为客户提供全方位的晶圆代工解决方案，包括光罩制造、IP研发及后段辅助设计服务等一站式服务(包含凸块加工服务、晶圆探测，以及最终的封装、测试等)。全面一体的晶圆代工解决方案,目标是更有效的帮助客户降低成本,以缩短产品上市时间。</text>
			</view>
		</view>
		<u-gap></u-gap>
		<u-section title="推荐产品与解决方案" :right="false" font-size="40"></u-section>
		<!-- 图文介绍，视频演示。 -->
		<view class="recommend_chanpin" @click="tochanping_De">
			<view class="chanpin">
				<u-image src="../../../../static/myimgs/myimg_zhizao/file_20220502cs24.jpg" width="100%" height="200rpx"></u-image>
				<h2>中国商飞语音通信解决方案</h2>
				<text class="u-line-3">中国商飞部署了几百台亿联SIP-T27P与SIP-T21P E2话机，用于各机构、各办事处之间的通讯交流，有效应对业务增长带来的各种沟通挑战， 同时又大大节约了通讯成本。</text>
			</view>
			<view class="chanpin">
				<u-image src="../../../../static/myimgs/myimg_zhizao/file_20220502cs25.jpg" width="100%" height="200rpx"></u-image>
				<h2>SCADA 管控一体化方案</h2>
				<text class="u-line-3">SCADA 管控一体化方案采用自主开发的微服务架构，提供工业数据实时采集，生产过程实时监管，报表数据智能分析，系统故障自动告警等功能。该方案与自主可用工业计算机，中国电子云形成“云边端”一体化的工业管控解决方案，可广泛应用于能源、电力、石化等行业。</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				banner: [
					"../../../../static/myimgs/myimg_zhizao/file_20220502cs23.jpg",
					"../../../../static/myimgs/myimg_zhizao/file_20220502cs24.jpg",
					"../../../../static/myimgs/myimg_zhizao/file_20220502cs25.jpg",
					"../../../../static/myimgs/myimg_zhizao/file_20220502cs26.jpg",
				]
			}
		},
		methods: {
			toruzhu(){
				uni.navigateTo({
					url:'ruzhu/ruzhu'
				})
			},
			tozhaopin(){
				uni.navigateTo({
					url:'zhaopin/zhaopin'
				})
			},
			tozhanhuihuodong(){
				uni.navigateTo({
					url:'zhanhuihuodong/zhanhuihuodong'
				})
			},
			tochanpinlist(){
				uni.navigateTo({
					url:'chanpinlist/chanpinlist'
				})
			},
			tochangshanglist(){
				uni.navigateTo({
					url:'changshanglist/changshanglist'
				})
			},
			tochanping_De(){
				uni.navigateTo({
					url:'chanpin_de'
				})
			},
			tochangshang_de(){
				uni.navigateTo({
					url:'changshang_de'
				})
			},
		}
	}
</script>

<style scoped>
	.type {
		display: flex;
		flex-direction: row;
		justify-content: space-around;
	}

	.changshang_re {
		margin: 10rpx;
		padding: 10rpx;
		border: #ccc 2rpx solid;
		border-radius: 20rpx;
	}
	.recommend_changshang{
		display: flex;
		flex-direction: row;
	}
	.recommend_changshang>*{
		width: 50%;
	}
	.chanpin{
		margin: 10rpx;
		padding: 10rpx;
		border: #ccc 2rpx solid;
		border-radius: 20rpx;
	}
</style>
