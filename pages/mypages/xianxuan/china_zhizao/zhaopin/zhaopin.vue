<template>
	<view>
		<view class="changshangall" @click="tozhaopin_de">
			<view class="changshang">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220502cs06.jpg" width="100%" height="200rpx">
						</u-image>
					</u-col>
					<u-col span="8">
						<h2>中芯国际</h2>
						<text
							class="u-line-4">中芯国际是一家纯晶圆代工厂，向全球客户提供0.35微米到14纳米8寸和12寸芯片代工与技术服务。中芯国际除高端的制造能力之外，还为客户提供全方位的晶圆代工解决方案，包括光罩制造、IP研发及后段辅助设计服务等一站式服务(包含凸块加工服务、晶圆探测，以及最终的封装、测试等)。全面一体的晶圆代工解决方案,目标是更有效的帮助客户降低成本,以缩短产品上市时间。</text>
					</u-col>
				</u-row>
			</view>
			<view class="changshang">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220502cs09.jpg" width="100%" height="200rpx">
						</u-image>
					</u-col>
					<u-col span="8">
						<h2>华为</h2>
						<text
							class="u-line-4">华为消费者业务产品全面覆盖手机、移动宽带终端、终端云等，凭借自身的全球化网络优势、全球化运营能力，致力于将最新的科技带给消费者，让世界各地享受到技术进步的喜悦，以行践言，实现梦想。</text>
					</u-col>
				</u-row>
			</view>
			<view class="changshang">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220501cs10.jpg" width="100%" height="200rpx">
						</u-image>
					</u-col>
					<u-col span="8">
						<h2>上海电气</h2>
						<text
							class="u-line-4">上海电气集团是中国工业制造业的领军品牌，历史至少可以追溯到1902年，创造了中国与世界众多第一。荣获中国工业领域最高奖项—中国工业大奖，入选《全球制造500强》、《财富》中国500强。入选《全球制造500强》、《财富》中国500强，2021年ENR全球最大</text>
					</u-col>
				</u-row>
			</view>
			<view class="changshang">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220501cs09.jpg" width="100%" height="200rpx">
						</u-image>
					</u-col>
					<u-col span="8">
						<h2>大疆</h2>
						<text
							class="u-line-4">深圳市大疆创新科技有限公司（DJ-Innovations，简称DJI），2006年由香港科技大学毕业生汪滔等人创立，是全球领先的无人飞行器控制系统及无人机解决方案的研发和生产商，客户遍布全球100多个国家。通过持续的创新，大疆致力于为无人机工业、行业用户以及专业航拍应用提供性能最强、体验最佳的革命性智能飞控产品和解决方案</text>
					</u-col>
				</u-row>
			</view>
			<view class="changshang">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220501cs25.jpg" width="100%" height="200rpx">
						</u-image>
					</u-col>
					<u-col span="8">
						<h2>潍柴动力</h2>
						<text
							class="u-line-4">潍柴动力股份有限公司成立于2002年（HK2338,SZ000338），由潍柴控股集团有限公司作为主发起人、联合境内外投资者创建而成，是中国内燃机行业在香港H股上市的企业，也是由境外回归内地实现A股再上市的公司。</text>
					</u-col>
				</u-row>
			</view>
			<view class="changshang">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220501cs24.jpg" width="100%" height="200rpx">
						</u-image>
					</u-col>
					<u-col span="8">
						<h2>蓝思科技</h2>
						<text
							class="u-line-4">公司是蓝思科技（香港）有限公司投资的一家集研发、生产、销售显示屏功能玻璃面板于一体的外商独资企业，2006年12月注册成立，注册资本6000万美元，落户长沙国家生物产业基地。</text>
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
			tozhaopin_de(){
				uni.navigateTo({
					url:'zhaopin_de'
				})
			},
		}
	}
</script>

<style scoped>
	.changshang {
		margin: 10rpx;
		padding: 10rpx;
		border: #ccc 2rpx solid;
		border-radius: 20rpx;
	}
</style>
