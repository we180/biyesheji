<template>
	<view>
		<view class="all" @click="tozhaopin_De">
			<view class="changshang">
				<u-image width="100%" height="220rpx" src="../../../../static/myimgs/china_zhizao/file_20220502cs32.jpg"></u-image>
				<h2 style="text-align: center;">上海机电</h2>
				<text class="u-line-3">上海机电股份有限公司是一家引领中国机电装备制造企业快速发展的大型上市公司，是其母公司中国最大的装备制造业集团，香港上市公司——上海电气集团股份有限公司的重要产业支柱之一，承担着机电一体化板块的发展重任。</text>
				
			</view>
			<view class="changshang">
				<u-image width="100%" height="220rpx" src="../../../../static/myimgs/china_zhizao/file_20220502cs34.jpg"></u-image>
				<h2 style="text-align: center;">中联重科</h2>
				<text class="u-line-3">中联重科创立于1992年，主要从事工程机械、农业机械等高新技术装备的研发制造，其主导产品覆盖11大类别、70个产品系列、568余个品种，是一家持续创新的全球化企业。</text>
				
			</view>
			<view class="changshang">
				<u-image width="100%" height="220rpx" src="../../../../static/myimgs/china_zhizao/file_20220502cs32.jpg"></u-image>
				<h2 style="text-align: center;">上海机电</h2>
				<text class="u-line-3">上海机电股份有限公司是一家引领中国机电装备制造企业快速发展的大型上市公司，是其母公司中国最大的装备制造业集团，香港上市公司——上海电气集团股份有限公司的重要产业支柱之一，承担着机电一体化板块的发展重任。</text>
				
			</view>
			<view class="changshang">
				<u-image width="100%" height="220rpx" src="../../../../static/myimgs/china_zhizao/file_20220502cs34.jpg"></u-image>
				<h2 style="text-align: center;">中联重科</h2>
				<text class="u-line-3">中联重科创立于1992年，主要从事工程机械、农业机械等高新技术装备的研发制造，其主导产品覆盖11大类别、70个产品系列、568余个品种，是一家持续创新的全球化企业。</text>
				
			</view>
			<view class="changshang">
				<u-image width="100%" height="220rpx" src="../../../../static/myimgs/china_zhizao/file_20220502cs32.jpg"></u-image>
				<h2 style="text-align: center;">上海机电</h2>
				<text class="u-line-3">上海机电股份有限公司是一家引领中国机电装备制造企业快速发展的大型上市公司，是其母公司中国最大的装备制造业集团，香港上市公司——上海电气集团股份有限公司的重要产业支柱之一，承担着机电一体化板块的发展重任。</text>
				
			</view>
			<view class="changshang">
				<u-image width="100%" height="220rpx" src="../../../../static/myimgs/china_zhizao/file_20220502cs34.jpg"></u-image>
				<h2 style="text-align: center;">中联重科</h2>
				<text class="u-line-3">中联重科创立于1992年，主要从事工程机械、农业机械等高新技术装备的研发制造，其主导产品覆盖11大类别、70个产品系列、568余个品种，是一家持续创新的全球化企业。</text>
				
			</view>
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
			tozhaopin_De(){
				uni.navigateTo({
					url:'zhaping_details'
				})
			},
		}
	}
</script>

<style scoped>
	.changshang{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #AAAAAA;
	}
</style>
