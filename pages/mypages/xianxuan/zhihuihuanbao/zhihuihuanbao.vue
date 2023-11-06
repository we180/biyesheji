<template>
	<view>
		<view class="banner">
			<u-swiper :list="banner" :effect3d="true"></u-swiper>
		</view>
		<u-gap></u-gap>
		<view class="type">
			<u-icon name="photo" color="#2979ff" size="100" label="垃圾物品展示" label-pos="bottom" label-size="36rpx" @click="tolajizhanshi"></u-icon>
			<u-icon name="file-text" color="#2979ff" size="100" label="信息预留" label-pos="bottom" label-size="36rpx" @click="toxinxiyuliu"></u-icon>
			<u-icon name="android-fill" color="#2979ff" size="100" label="附近回收机" label-pos="bottom" label-size="36rpx" @click="tohuishouji"></u-icon>
		</view>
		<view class="type">
			<u-icon name="map" color="#2979ff" size="100" label="预约上门回收垃圾" label-pos="bottom" label-size="36rpx" @click="toshangmenhuishou"></u-icon>
			<u-icon name="list-dot" color="#2979ff" size="100" label="预约回收垃圾历史" label-pos="bottom" label-size="36rpx" @click="tohuishou_history"></u-icon>
		</view>
		<u-gap></u-gap>
		<u-section title="环境宣传" font-size="40" :right="false"></u-section>
		<view class="huanjingxuanchuan" v-for="(item,index) in 1" :key="index">
			<u-row>
				<u-col span="4">
					<u-image width="100%" height="250rpx" src="../../../../static/myimgs/myimg_huanbao/u=1299061469,111270754&fm=26&fmt=auto&gp=0.jpg"></u-image>
				</u-col>
				<u-col span="8">
					<h3 class="u-line-2">西安市智慧环保综合指挥中心开展“西安生态日”进企业主题宣传活动</h3>
					<text class="u-line-4">西安市智慧环保综合指挥中心工作人员前往经开区、未央区和国际港务区检查，并开展以防治扬尘污染为主题的“西安生态日”进企业宣传活动，鼓励广大职工主动投身到蓝天保卫战中。</text>
				</u-col>
			</u-row>
			<u-gap></u-gap>
			<u-row>
				<u-col span="4">
					<u-image width="100%" height="250rpx" src="../../../../static/myimgs/myimg_huanbao/1.png"></u-image>
				</u-col>
				<u-col span="8">
					<h3 class="u-line-2">“检查+宣传” ！西安市智慧环保综合指挥中心双管齐下，守护“西安蓝”</h3>
					<text class="u-line-4">3月份以来，西安市空气质量受PM10污染影响较大，工地扬尘又是PM10的重要来源。为强化施工单位扬尘防护意识，减少建筑施工工地现场扬尘污染，不给“西安蓝”增灰，近日，西安市智慧环保综合指挥中心工作人员针对未央区、浐灞生态区和曲江新区的部分建筑工地进行随机摸底督导检查，并向工地相关负责人发放扬尘防治海报，宣传讲解扬尘污染防治的意义和相关措施。</text>
				</u-col>
			</u-row>
			<u-gap></u-gap>
			<u-row>
				<u-col span="4">
					<u-image width="100%" height="250rpx" src="../../../../static/myimgs/myimg_huanbao/2.png"></u-image>
				</u-col>
				<u-col span="8">
					<h3 class="u-line-2">3	西安市智慧环保综合指挥中心进社区宣传生物多样性保护</h3>
					<text class="u-line-4">5月22日国际生物多样性日来临前夕，为进一步提高公众参与生物多样性保护工作的积极性，增强社区居民的生态环保意识。5月20日，西安市智慧环保综合指挥中心前往白桦林居社区开展了主题生态环境保护宣传教育活动。</text>
				</u-col>
			</u-row>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				banner:[
					"../../../../static/myimgs/myimg_huanbao/u=1299061469,111270754&fm=26&fmt=auto&gp=0.jpg",
					"../../../../static/myimgs/myimg_huanbao/u=262416087,1088520702&fm=26&fmt=auto&gp=0.jpg",
					"../../../../static/myimgs/myimg_huanbao/u=416427056,2426282343&fm=26&fmt=auto&gp=0.jpg",
					"../../../../static/myimgs/myimg_huanbao/u=437473768,55194742&fm=11&fmt=auto&gp=0.jpg"
					
				],
			}
		},
		methods: {
			toxinxiyuliu(){
				uni.navigateTo({
					url:'xinxiyuliu/xinxiyuliu'
				})
			},
			tolajizhanshi(){
				uni.navigateTo({
					url:'lajizhanshi/lajizhanshi'
				})
			},
			tohuishouji(){
				uni.navigateTo({
					url:'huishouji/huishouji'
				})
			},
			toshangmenhuishou(){
				uni.navigateTo({
					url:'yuyue_shangmen/yuyue_shangmen'
				})
			},
			tohuishou_history(){
				uni.navigateTo({
					url:'yuyue_history/yuyue_history'
				})
			},
		}
	}
</script>

<style scoped>
	.type{
		display: flex;
		flex-direction: row;
		justify-content: space-around;
	}
	.huanjingxuanchuan{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
