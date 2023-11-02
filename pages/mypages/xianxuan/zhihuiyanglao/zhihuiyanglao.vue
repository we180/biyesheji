<template>
	<view>
		<view class="search">
			<u-search @custom="search" @search="search"></u-search>
		</view>
		<u-gap></u-gap>
		<view class="banner">
			<u-swiper :list="banner"></u-swiper>
		</view>
		<u-gap></u-gap>
		<view class="type">
			<u-icon name="file-text" label="健康评估" label-pos="bottom" color="#2979ff" size="105" label-size="30" @click="tojiankangpinggu"></u-icon>
			<u-icon name="eye" label="平台检测" label-pos="bottom" color="#2979ff" size="105" label-size="30" @click="topingtaijiance"></u-icon>
			<u-icon name="edit-pen" label="预约养老院" label-pos="bottom" color="#2979ff" size="105" label-size="30" @click="toyuyue"></u-icon>
			<u-icon name="coupon" label="巡检记录" label-pos="bottom" color="#2979ff" size="105" label-size="30" @click="toxunjian"></u-icon>
			<u-icon name="grid" label="集中检测" label-pos="bottom" color="#2979ff" size="105" label-size="30" @click="tojizhongjiance"></u-icon>
		</view>
		<u-gap></u-gap>
		<view class="recommend" @click="todetails">
			<u-section font-size="40" title="养老机构推荐"></u-section>
			<u-gap></u-gap>
			<view class="recommend_de">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../static/myimgs/myimg_yanglao/u=344519103,3661532422&fm=26&fmt=auto&gp=0.jpg" width="100%" height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>河北枫叶老年公寓</h3>
						<text class="u-line-3">长安区枫叶老年公寓位于动力医院三、四楼,是集医疗、护理、托管、娱乐、康复为一体的大型医疗养老机构,老年公寓将养老和医疗完美结合,让入住的老人在养老的同时加上一份及时的医疗保障</text>
						<u-rate :count="5" :current="4.3" :disabled="true"></u-rate> 
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="recommend_de">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../static/myimgs/myimg_yanglao/u=662466973,3714270328&fm=26&fmt=auto&gp=0.jpg" width="100%" height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>同辉养老</h3>
						<text class="u-line-3">同辉养老（集团）是一家有梦想、有强烈社会责任感的医养健康服务型企业，定位于一家连锁化的医养结合型中高端养老服务品牌。我们坚持以“同辉医养，让长者生命更健康”的根本服务宗旨，以打造“中国一流医养服务品牌”为发展愿景，以“代忙碌儿女尽孝，替孤独父母解愁，为党和政府分忧”为己任，致力于“提供高品质、专业化的医养健康服务，履行社会责任”的企业使命，为离退休长者提供无微不至的“医养康护娱居”一站式服务，像爱自己的孩子一样爱长者，替天下忙碌儿女尽一份爱心，为国家社会贡献一份责任。</text>
						<u-rate :count="5" :current="4.3" :disabled="true"></u-rate> 
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="recommend_de">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../static/myimgs/myimg_yanglao/u=1549922178,2841446138&fm=26&fmt=auto&gp=0.jpg" width="100%" height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>赣州幸福村智慧养老平台</h3>
						<text class="u-line-3">赣州幸福村智慧养老平台养老版块涵盖居家养老和机构养老，其中机构养老包括赣州添立养老院，大公路养老院，水东养老院，蟠龙养老院，赣州三附院永昌院区；居家养老以各机构园区为中心覆盖周边居家养老区域，杰佳通为添立医养建设的智慧健康养老平台，以养老平台为中心，融合居家和机构养老大数据，医养结合的养老模式、虚拟养老院、智慧养老运作模式、养老评估管理系统、慢病管理系统、老人安全保障系统、社区养老管理系统、老年大学系统、志愿者管理系统、养老政府监管平台等等。</text>
						<u-rate :count="5" :current="4.3" :disabled="true"></u-rate> 
					</u-col>
				</u-row>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				banner:[
					"../../../../static/myimgs/myimg_yanglao/u=259881674,1275827384&fm=26&fmt=auto&gp=0.jpg",
					"../../../../static/myimgs/myimg_yanglao/u=344519103,3661532422&fm=26&fmt=auto&gp=0.jpg",
					"../../../../static/myimgs/myimg_yanglao/u=508828966,654175694&fm=11&fmt=auto&gp=0.jpg"
					
				],
			}
		},
		methods: {
			search(){
				uni.navigateTo({
					url:'search_yanglao'
				})
			},
			tojiankangpinggu(){
				uni.navigateTo({
					url:'jiankangpinggu/jiankangpinggu'
				})
			},
			toyuyue(){
				uni.navigateTo({
					url:'yuyue/yuyue'
				})
			},
			topingtaijiance(){
				uni.navigateTo({
					url:'pingtaijiance/pingtaijiance'
				})
			},
			toxunjian(){
				uni.navigateTo({
					url:'xunjianjilu/xunjianjilu'
				})
			},
			tojizhongjiance(){
				uni.navigateTo({
					url:'jizhongjiance/jizhongjiance'
				})
			},
			todetails(){
				uni.navigateTo({
					url:'yuyue/yuyue_index'
				})
			}
		}
	}
</script>

<style scoped>
	.type{
		display: flex;
		flex-direction: row;
		justify-content: space-around;
	}
	.recommend_de{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: #A0CFFF 2rpx solid;
	}
</style>

						<text class="u-line-3">长安区枫叶老年公寓位于动力医院三、四楼,是集医疗、护理、托管、娱乐、康复为一体的大型医疗养老机构,老年公寓将养老和医疗完美结合,让入住的老人在养老的同时加上一份及时的