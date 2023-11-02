<template>
	<view>
		<view class="search">
			<u-search placeholder="搜索养老机构"></u-search>
		</view>
		<view class="recommend" @click="toindex">
			<u-gap></u-gap>
			<view class="recommend_de">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_yanglao/u=344519103,3661532422&fm=26&fmt=auto&gp=0.jpg"
							width="100%" height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>河北枫叶老年公寓</h3>
						<text
							class="u-line-3">长安区枫叶老年公寓位于动力医院三、四楼,是集医疗、护理、托管、娱乐、康复为一体的大型医疗养老机构,老年公寓将养老和医疗完美结合,让入住的老人在养老的同时加上一份及时的医疗保障</text>
						<u-rate :count="5" :current="4.3" :disabled="true"></u-rate>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="recommend_de">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_yanglao/u=662466973,3714270328&fm=26&fmt=auto&gp=0.jpg"
							width="100%" height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>同辉养老</h3>
						<text
							class="u-line-3">同辉养老（集团）是一家有梦想、有强烈社会责任感的医养健康服务型企业，定位于一家连锁化的医养结合型中高端养老服务品牌。我们坚持以“同辉医养，让长者生命更健康”的根本服务宗旨，以打造“中国一流医养服务品牌”为发展愿景，以“代忙碌儿女尽孝，替孤独父母解愁，为党和政府分忧”为己任，致力于“提供高品质、专业化的医养健康服务，履行社会责任”的企业使命，为离退休长者提供无微不至的“医养康护娱居”一站式服务，像爱自己的孩子一样爱长者，替天下忙碌儿女尽一份爱心，为国家社会贡献一份责任。</text>
						<u-rate :count="5" :current="4.3" :disabled="true"></u-rate>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="recommend_de">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_yanglao/u=1549922178,2841446138&fm=26&fmt=auto&gp=0.jpg"
							width="100%" height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>赣州幸福村智慧养老平台</h3>
						<text
							class="u-line-3">赣州幸福村智慧养老平台养老版块涵盖居家养老和机构养老，其中机构养老包括赣州添立养老院，大公路养老院，水东养老院，蟠龙养老院，赣州三附院永昌院区；居家养老以各机构园区为中心覆盖周边居家养老区域，杰佳通为添立医养建设的智慧健康养老平台，以养老平台为中心，融合居家和机构养老大数据，医养结合的养老模式、虚拟养老院、智慧养老运作模式、养老评估管理系统、慢病管理系统、老人安全保障系统、社区养老管理系统、老年大学系统、志愿者管理系统、养老政府监管平台等等。</text>
						<u-rate :count="5" :current="4.3" :disabled="true"></u-rate>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="recommend_de">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_yanglao/u=2662948664,2345223694&fm=26&fmt=auto&gp=0.jpg"
							width="100%" height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>佳林养老院</h3>
						<text
							class="u-line-3">佳林养老院设计合理,环境优美、空气新鲜.院内设有绿色休闲长廊、绿树成荫,四季常青.同时为满足住院老人的绿色饮食和业余生活,规划了休闲养殖园等。同时根据入住老人需要配置多媒体教室、图书阅览室、康复健身室、文化娱乐室等活动场所,确保入住老人业余生活丰富多彩、颐养天年。</text>
						<u-rate :count="5" :current="4.3" :disabled="true"></u-rate>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="recommend_de">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_yanglao/u=1504822684,3402664429&fm=26&fmt=auto&gp=0.jpg"
							width="100%" height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>新华区银龄老年公寓</h3>
						<text
							class="u-line-3">银龄老年公寓设立于2012年,采用欧式别墅景观设计,可提供床位200张，辅助功能设有活动室、健身房、医务室、心理治疗室、监控中心等.</text>
						<u-rate :count="5" :current="4.3" :disabled="true"></u-rate>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="recommend_de">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_yanglao/u=3323158740,3481743898&fm=26&fmt=auto&gp=0.jpg"
							width="100%" height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>石家庄藁城区盛德老年公寓</h3>
						<text
							class="u-line-3">长安区枫叶老年公寓位于动力医院三、四楼,是集医疗、护理、托管、娱乐、康复为一体的大型医疗养老机构,老年公寓将养老和医疗完美结合,让入住的老人在养老的同时加上一份及时的医疗保障</text>
						<u-rate :count="5" :current="4.3" :disabled="true"></u-rate>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="recommend_de">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_yanglao/u=2200436517,1707493217&fm=26&fmt=auto&gp=0.jpg"
							width="100%" height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>金秋阳光养老产业园</h3>
						<text
							class="u-line-3">金秋阳光养老产业园项目总投资20亿元，规划总建筑面积28,8077平方米，占地面积16,9959平方米。本项目规划建设一所容纳500床位的二级甲等医院，养老产业园项目可容纳3500--5000人，其中包含1栋12层的住院楼，1栋8层的护理楼，1栋8层的康复楼，16栋9层的高端养老公寓，6栋6层的普通养老公寓，5栋12层的组团养老公寓，6栋16层的配套职工公寓，以及1栋9层的养老服务中心，1栋3层的老年活动中心和1栋2层的老年餐厅，1栋3层的老年大学。</text>
						<u-rate :count="5" :current="4.3" :disabled="true"></u-rate>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="recommend_de">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_yanglao/u=2693442287,3381964257&fm=26&fmt=auto&gp=0.jpg"
							width="100%" height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>示范型居家养老服务中心</h3>
						<text
							class="u-line-3">白杨街道居家养老服务中心建筑面积约1920平方米，共三层，设置了生活服务、康复护理服务、托养服务、家庭支持服务、社会工作和心理疏导服务、康复辅助器具租赁服务等六大功能区块。</text>
						<u-rate :count="5" :current="4.3" :disabled="true"></u-rate>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
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
			toindex(){
				uni.navigateTo({
					url:'yuyue_index'
				})
			},
		}
	}
</script>

<style scoped>
	.recommend_de {
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: #A0CFFF 2rpx solid;
	}
</style>
