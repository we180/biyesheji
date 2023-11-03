<template>
	<view>
		<u-section title="公司党建" font-size="36" lineColor="red"></u-section>
		<u-gap></u-gap>
		<view class="dongtai1">
			<view class="index" @click="todongtai_De">
				<u-row>
					<u-col span="4">
						<image src="../../../../static/myimgs/myimg_dangjian/u=237204657,1833581701&fm=26&fmt=auto&gp=0.jpg" mode=""
							style="width: 230rpx; height: 230rpx;"></image>
					</u-col>
					<u-col span="8">
						<h3>江西铜业集团有限公司党建信息化平台一期建设项目</h3>
						<text
							class="u-line-3">江西铜业为世界500强企业，是有色金属行业的龙头企业，共有党员1万人左右。为深入贯彻党中央、省委关于加快推进基层党建信息化建设的部署，充分发挥信息网络技术在加强和改进新形势下党的建设工作的支撑作用</text>
					</u-col>
				</u-row>
				<u-gap></u-gap>
				<u-row>
					<u-col span="4">
						<image src="../../../../static/myimgs/myimg_dangjian/1.png" mode=""
							style="width: 230rpx; height: 230rpx;"></image>
					</u-col>
					<u-col span="8">
						<h3>太平养老保险股份有限公司党建云</h3>
						<text
							class="u-line-3">太平养老保险股份有限公司(简称“太平养老”)成立于2004年，是中管金融机构中国太平保险集团有限责任公司旗下专业经营养老金业务和员工福利保障业务的重要子公司，也是我国首家国有专业养老保险公司，服务网络覆盖全国。</text>
					</u-col>
				</u-row>
			</view>
		</view>
		<u-gap></u-gap>
		<view class="dongtai2" @click="todongtai_De">
			<u-section title="其他党建" font-size="36" lineColor="red"></u-section>
			<u-gap></u-gap>
			<view class="index">
				<u-row>
					<u-col span="4">
						<image src="../../../../static/myimgs/myimg_dangjian/u=1283301471,2626968760&fm=26&fmt=auto&gp=0.jpg" mode=""
							style="width: 230rpx; height: 230rpx;"></image>
					</u-col>
					<u-col span="8">
						<h3>中华人民共和国驻摩洛哥王国大使馆党建</h3>
						<text
							class="u-line-3">习近平总书记指出，要高度重视信息化发展对党的建设的影响，做到网络发展到哪里，党的工作就覆盖到哪里，充分运用信息技术改进党员教育管理、提高群众工作水平，加强网络舆论的正面引导。</text>
					</u-col>
				</u-row>
				<u-gap></u-gap>
				<u-row>
					<u-col span="4">
						<image src="../../../../static/myimgs/myimg_dangjian/2.png" mode=""
							style="width: 230rpx; height: 230rpx;"></image>
					</u-col>
					<u-col span="8">
						<h3>中国建筑标准设计研究院党建云</h3>
						<text
							class="u-line-3">中国建筑标准设计研究院(简称“标准院”)，创建于1956年，前身为建设部直属事业单位——建筑标准设计研究所，2000年转制为中央科技型企业，现隶属中国建设科技集团。</text>
					</u-col>
				</u-row>
				<u-gap></u-gap>
				<u-row>
					<u-col span="4">
						<image src="../../../../static/myimgs/myimg_dangjian/3.png" mode=""
							style="width: 230rpx; height: 230rpx;"></image>
					</u-col>
					<u-col span="8">
						<h3>中国邮政集团公司党建信息化平台</h3>
						<text
							class="u-line-3">按照新时代党的建设总要求，中国邮政党建信息化系统围绕“党的政治建设、思想建设、组织建设、作风建设、纪律建设以及反腐败工作”六项内容，拟采用“互联网+基层党建”的管理模式</text>
					</u-col>
				</u-row>
				<u-gap></u-gap>
				<u-row>
					<u-col span="4">
						<image src="../../../../static/myimgs/myimg_dangjian/4.png" mode=""
							style="width: 230rpx; height: 230rpx;"></image>
					</u-col>
					<u-col span="8">
						<h3>江西铜业集团有限公司党建信息化平台一期建设项目</h3>
						<text
							class="u-line-3">江西铜业为世界500强企业，是有色金属行业的龙头企业，共有党员1万人左右。为深入贯彻党中央、省委关于加快推进基层党建信息化建设的部署，充分发挥信息网络技术在加强和改进新形势下党的建设工作的支撑作用，提高基层党建信息化水平，江铜党委把推进党建信息化建设，打造江铜党建升级版，列为2018年创建世界一流企业的重要工作之一。</text>
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
				
			}
		},
		methods: {
			todongtai_De(){
				uni.navigateTo({
					url:'dongtai_details'
				})
			},
		}
	}
</script>

<style scoped>

</style>
