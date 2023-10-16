<template>
	<view>
		<view class="banner">
			<u-swiper :list="banner" :effect3d="true"></u-swiper> 
		</view>
		<u-gap></u-gap>
		<view class="type">
			<u-icon name="list-dot" color="#2979ff" size="88" label-pos="bottom" label="厂商列表" label-size="32" @click="tochangshanglist"></u-icon>
			<u-icon name="order" color="#2979ff" size="88" label-pos="bottom" label="产品列表" label-size="32" @click="tochanpinlist"></u-icon>
			<u-icon name="bookmark" color="#2979ff" size="88" label-pos="bottom" label="展会活动" label-size="32" @click="tohuodong"></u-icon>
			<u-icon name="man-add" color="#2979ff" size="88" label-pos="bottom" label="厂商招聘" label-size="32" @click="tozhaopin"></u-icon>
			<u-icon name="home" color="#2979ff" size="88" label-pos="bottom" label="厂商入驻" label-size="32" @click="toruzhu"></u-icon>
		</view>
		<u-gap></u-gap>
		<u-section title="推荐厂商" :right="false" font-size="40"></u-section>
		<view class="recommed_changshang" @click="tochangshang">
			<view class="changshang">
				<u-image width="100%" height="220rpx" src="../../../static/myimgs/china_zhizao/file_20220502cs32.jpg"></u-image>
				<h2 style="text-align: center;">上海机电</h2>
				<text class="u-line-3">上海机电股份有限公司是一家引领中国机电装备制造企业快速发展的大型上市公司，是其母公司中国最大的装备制造业集团，香港上市公司——上海电气集团股份有限公司的重要产业支柱之一，承担着机电一体化板块的发展重任。</text>
				
			</view>
			<view class="changshang">
				<u-image width="100%" height="220rpx" src="../../../static/myimgs/china_zhizao/file_20220502cs34.jpg"></u-image>
				<h2 style="text-align: center;">中联重科</h2>
				<text class="u-line-3">中联重科创立于1992年，主要从事工程机械、农业机械等高新技术装备的研发制造，其主导产品覆盖11大类别、70个产品系列、568余个品种，是一家持续创新的全球化企业。</text>
				
			</view>
		</view>
		<u-gap></u-gap>
		<u-section title="推荐产品与解决方案" :right="false" font-size="40"></u-section>
		<view class="recommed_chanpin" @click="tochanpin">
			<view class="chanpin">
				<u-image width="100%" height="220rpx" src="../../../static/myimgs/china_zhizao/file_20220502cs49.jpg"></u-image>
				<h2 style="text-align: center;">工业互联网平台</h2>
				<text class="u-line-3">在实践中，吉利工业互联网平台正在颠覆过去的“以产品为中心”的制造模式，重构“以用户为中心”的、以工业互联网平台为引擎的智能制造新模式。这个模式将改写工厂化、刚性的大规模生产，转向网络化、可重构的多品种柔性生产。</text>
				
			</view>
			<view class="chanpin">
				<u-image width="100%" height="220rpx" src="../../../static/myimgs/china_zhizao/file_20220502cs46.jpg"></u-image>
				<h2 style="text-align: center;">高效节能解决方案</h2>
				<text class="u-line-3">业务涵盖综合用能服务方案与智慧照明方案，其中：综合用能服务方案聚焦CDA系统、冷热源系统、污泥污水处理、设备节能升级四大细分技术领域，智慧照明方案提供高功效半导体照明产品。通过自主研发的能效管理系统、</text>
				
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				banner:[
					"../../../static/myimgs/china_zhizao/file_20220502cs42.jpg",
					"../../../static/myimgs/china_zhizao/file_20220502cs49.jpg",
					"../../../static/myimgs/china_zhizao/file_20220502cs46.jpg"
				]
			}
		},
		methods: {
			tochangshang(){
				uni.navigateTo({
					url:'changshang_De'
				})
			},
			tochanpin(){
				uni.navigateTo({
					url:'chanpin_De'
				})
			},
			tochangshanglist(){
				uni.navigateTo({
					url:'changshang_list/changshang_list'
				})
			},
			tochanpinlist(){
				uni.navigateTo({
					url:'chanpin_list/chanpin_list'
				})
			},
			tohuodong(){
				uni.navigateTo({
					url:'huodong/huodong'
				})
			},
			tozhaopin(){
				uni.navigateTo({
					url:'zhaopin/zhaopin'
				})
			},
			toruzhu(){
				uni.navigateTo({
					url:'ruzhu/ruzhu'
				})
			},
		}
	}
</script>

<style scoped>
	.type{
		display: flex;
		justify-content: space-around;
	}
	.changshang{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #AAAAAA;
	}
	.chanpin{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #AAAAAA;
	}
</style>
