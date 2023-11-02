<template>
	<view>
		<!-- 招聘需求，校企合作动态，校企合作科研转化成果典型案例图文介绍，视频宣传片。 -->
		<u-section title="招聘需求" font-size="40" :right="false"></u-section>
		<view class="info">
			<text>招聘职位:网络安全工程师</text>
			<text>薪水:18k-25k/月</text>
			<text>学历:大专及以上</text>
			<text>工作经历:至少5年以上工作经验</text>
			<text>联系电话:1397426850</text>
		</view>
		<u-gap></u-gap>
		<u-section title="校企合作动态" font-size="40" :right="false"></u-section>
		<view class="info">
			<text>广州设计周展会始于 2006 年，中国第一个“设计+选材”（D+B，Design+Brands）为策展主题的大型 B2B 展，专注于设计师渠道价值开发及推动设计师与品牌商的对接合作，是中国目前规模最大、参与人数极多、影响力极广、国际化程度极高的“设计+选材”博览会。</text>
		</view>
		<u-gap></u-gap>
		<u-section title="校企合作科研转化成果案例" font-size="40" :right="false"></u-section>
		<view class="info">
			<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220502cs26.jpg" width="100%" height="200rpx"></u-image>
			<text>第九届中国国际养老服务业博览会将于2022年11月28-30日在北京国家会议中心举办。中国国际养老服务业博览会已成功举办八届，在民政部、全国老龄工作委员会办公室的关怀指导下，在国际社会和全社会的积极参与下，博览会已成促进国内外养老服务界快速融合的品牌展会。</text>
			<video :src="'../../../../../static/myimgs/myimg_zhizao/video02.mp4'" controls style="width: 100%;"></video>
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
			
		}
	}
</script>

<style scoped>
	.info{
		margin: 10rpx;
		padding: 10rpx;
		border: #ccc 2rpx solid;
		border-radius: 20rpx;
		display: flex;
		flex-direction: column;
		font-size: 34rpx;
	}
</style>
