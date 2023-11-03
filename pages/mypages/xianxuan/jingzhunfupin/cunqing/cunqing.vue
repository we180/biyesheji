<template>
	<view>
		<!-- 图片、村名称，地址、简介，点击“查看更多”按钮可查看全部村子信息 -->
		<view class="cunqinglist" @click="tocunqing_De">
			<view class="cunqing">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_fupin/8abe3f56303248033f031f01f7522700@2x.png" width="100%" height="200rpx" border-radius="20rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>秦峰镇新塘村</h3>
						<h4>江苏省无锡市宜兴市</h4>
						<text class="u-line-3">近日，秦峰镇新塘村村民委员会为感谢锁进先生为秦峰镇新塘村的扶贫事业做出的杰出贡献，特聘锁进先生为新塘村的“名誉村主任”。锁进先生是江西渝网科技股份有限公司董事长，上饶开阳即渝网旗下全资子公司，此前一直专注于扶贫事业，经商的同时不忘回馈社会，积极履行应尽的社会责任，呼吁更多社会人士共同营造互相关心、互相帮助、互相支持的良好社会氛围</text>
						
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="cunqing">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_fupin/12.png" width="100%" height="200rpx" border-radius="20rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>汉寿县洞庭村</h3>
						<h4>湖南省永州市江永县</h4>
						<text class="u-line-3">近年来，常德联通共向挂钩帮扶村和贫困户拨付款项近百万元，用于支持村委道路建设、文体广场修建、平安监控安装、环境卫生整治等，帮助全村主干道清除淤泥8KM, 让62户238人稳定脱贫，贫困人口实现全部脱贫，错评错退率实现0%，群众满意度达到了100%，脱贫攻坚工作取得决定性成效。</text>
						
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="cunqing">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_fupin/13.png" width="100%" height="200rpx" border-radius="20rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>海星村</h3>
						<h4>广东省河源市龙川县佗城</h4>
						<text class="u-line-3">海星村位于宝山区罗泾镇东北部，是罗泾镇打造“五村联动”乡村振兴示范片区之一。将生产旅游、农业旅游和文化旅游相融合，通过人流带动，转化成村民收益，实现农业强、农村美、农民富的新农村。</text>
						
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="cunqing">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_fupin/14.png" width="100%" height="200rpx" border-radius="20rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>天平村</h3>
						<h4>福建省宁德市福安市</h4>
						<text class="u-line-3"天平村位于宝山区罗店镇东北翼，村域总用地面积2.63平方公里。以新农业为支撑、新生态为基础、新治理为举措，打造上海市城乡共融、产园共兴示范村。</text>
						
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="cunqing">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_fupin/15.png" width="100%" height="200rpx" border-radius="20rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>仙下乡龙溪村</h3>
						<h4>浙江省嘉兴市桐乡市</h4>
						<text class="u-line-3">仙下乡龙溪村，村总面积1.1平方公里。以海派乡村风貌为基底、“农旅+文旅”融合为产业发展方向、以“123”乡村善治模式为手段，打造“醉美聚源桥，沪北花园村”。</text>
						
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
		</view>
		<view class="lookmore" v-if="lookmore==0">
			<u-button type="success" @click="lookmore=1">查看更多</u-button>
		</view>
		<view class="morelist" v-if="lookmore==1" @click="tocunqing_De">
			<view class="cunqing">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_fupin/16.jpg" width="100%" height="200rpx" border-radius="20rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>大凉山</h3>
						<h4>四川大凉山</h4>
						<text class="u-line-3">大凉山位于四川省西南部，是彝族聚居的地区。由于历史、地理等多方面原因，大凉山一直处于贫困状态。这里的农村基础设施落后，农业生产水平低，居民生活条件艰苦。尽管近年来政府加大了扶贫扶贫2. 贵州黔东南：黔东南位于贵州省东南部，是一个苗族聚居的地区。由于地理位置偏远，交通不便，黔东南的农村经济发展较为滞后。这里的农村基础设施薄弱，农民生活条件艰苦，贫困问题较为突出。</text>
						
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="cunqing">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_fupin/17.jpg" width="100%" height="200rpx" border-radius="20rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>贵州省黔南布依族苗族自治州</h3>
						<h4>贵州省黔南布依族苗族自治州</h4>
						<text class="u-line-3">贵州省黔南布依族苗族自治州是一个地处偏远、交通不便的农村地区，经济发展相对滞后。该地区的农村基础设施薄弱，农民生活条件艰苦。由于缺乏现代化的农业技术和设备，粮食产量低下，农民收入微薄。此外，黔南布依族苗族自治州的贫困问题还受到自然环境的影响</text>
						
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
				lookmore:0
			}
		},
		methods: {
			tocunqing_De(){
				uni.navigateTo({
					url:'cunqing_details'
				})
			},
		}
	}
</script>

<style>

</style>
