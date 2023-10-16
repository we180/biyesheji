<template>
	<view>
		<u-section title="平台产品与解决方案" :right="false" font-size="40"></u-section>
		<view class="chanpin" v-for="(item,index) in 2" :key="index" @click="tochanpin_De">
			<u-image width="100%" height="220rpx" src="../../../../static/myimgs/china_zhizao/file_20220502cs49.jpg"></u-image>
			<h2 style="text-align: center;">工业互联网平台</h2>
			<text class="u-line-3">在实践中，吉利工业互联网平台正在颠覆过去的“以产品为中心”的制造模式，重构“以用户为中心”的、以工业互联网平台为引擎的智能制造新模式。这个模式将改写工厂化、刚性的大规模生产，转向网络化、可重构的多品种柔性生产。</text>
			
		</view>
		<u-gap></u-gap>
		<u-section title="电力产品与解决方案" :right="false" font-size="40"></u-section>
		<view class="chanpin" v-for="(item,index2) in 2" :key="index2+9" @click="tochanpin_De">
			<u-image width="100%" height="220rpx" src="../../../../static/myimgs/china_zhizao/file_20220502cs46.jpg"></u-image>
			<h2 style="text-align: center;">高效节能解决方案</h2>
			<text class="u-line-3">业务涵盖综合用能服务方案与智慧照明方案，其中：综合用能服务方案聚焦CDA系统、冷热源系统、污泥污水处理、设备节能升级四大细分技术领域，智慧照明方案提供高功效半导体照明产品。通过自主研发的能效管理系统、</text>
			
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
			tochanpin_De(){
				uni.navigateTo({
					url:'../chanpin_De'
				})
			},
		}
	}
</script>

<style scoped>
	.chanpin{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #AAAAAA;
	}
</style>
