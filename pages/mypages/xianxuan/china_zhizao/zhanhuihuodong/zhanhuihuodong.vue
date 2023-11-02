<template>
	<view>
		<u-tabs :list="list" :current="current" @change="changetab" style="text-align: center;"></u-tabs>
		<!-- 包括最新展会活动发布，展会信息，参展报名。过往展会图文与视频记录。 -->
		<view class="lastest" v-if="current==0" @click="tozhanhui_De">
			<view class="changshang">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220502cs44.jpg" width="100%"
							height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>2022珠三角深圳锂电池技术展览会暨论坛</h3>
						<text class="u-line-3">锂电池：锂离子电池、镍氢电池、镍镉电池、固态电池、超级电容器、钠硫电池、钠氯化镍电池、液流电池、锂一次电池、锌锰电池、锂锰扣式电池、碱锰电池、锌镍电池、 锌银电池、热电池、燃料电池、蓄电池、太阳能电池、薄膜电池、半导体温差电组件及其他新型电池等；</text>
					</u-col>
				</u-row>
			</view>
			<view class="changshang">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220503cs35.jpg" width="100%"
							height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>20222022第十届中国广州国际海事贸易展览会暨论坛</h3>
						<text class="u-line-3">• 船舶设计和建造• 船坞和修船厂• 船舶营运和管理• 船舶登记和检验• 船舶修理机械与设备• 疏浚设备• 导航和通讯系统• 轮机工程和船用设备• 推进系统/泵和阀• 海洋工程• 计算机系统、网络和软件• 环境保护装备和设施• 起重和升降设备• 海上货运和物流• 油漆和涂料• 冷冻系统和冷藏系统• 港口、码头设备和服务</text>
					</u-col>
				</u-row>
			</view>
			<view class="changshang">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220503cs40.jpg" width="100%"
							height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>2022第三十一届上海国际电力设备及技术展览会暨第二十三届中国国际电工装备展览会</h3>
						<text class="u-line-3">国内电力行业中具规模及影响力的品牌电力展—国际电力电工展（EP） 始于1986年，由中国电力企业联合会、国家电网主办, 雅式展览服务有限公司承办，是国内获得UFI国际认证之专业电力展。 承蒙业界人士及海内外参展商多年来的大力支持，</text>
					</u-col>
				</u-row>
			</view>
			<view class="changshang">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220503cs37.jpg" width="100%"
							height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>20222022第十八届中国（上海）国际铸造、铸件展览会</h3>
						<text class="u-line-3">“中国（上海）国际铸造展览会、中国（上海）国际铸件产品展”创办于2005年，已成功举办十六届，展品覆盖铸件、铸造模具、铸造材料、铸造设备及铸造配套等领域，已发展成为行业内高规格、高层次、专业化、权威性的品牌展会之一。展会积极响应国家政策号召，倡导企业走创新、高效的绿色铸造之路，</text>
					</u-col>
				</u-row>
			</view>
			<view class="changshang">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220503cs38.jpg" width="100%"
							height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>MTM2022金属世界博览会</h3>
						<text class="u-line-3">MTM 2022（Metallurgy+Tube+Metal）金属世界博览会，将于2022年12月1日-12月3日举办。作为全球钢铁冶金工业领域久负盛名的技术贸易盛会。它起源于1986年，是当前国内品牌历史最悠久的冶金专业展，也是行业内最权威的博览平台之一。</text>
					</u-col>
				</u-row>
			</view>
			<view class="changshang">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220503cs39.jpg" width="100%"
							height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>2022上海国际汽车零配件、维修检测诊断设备及服务用品展览会</h3>
						<text class="u-line-3">作为覆盖汽车全产业链的大型行业服务平台，Automechanika Shanghai为业内人士提供了信息交流、行业推广、商贸对接及产业教育的全方位机遇，丰富多彩的同期活动，获得了与会者的积极反馈和好评。上届回顾：尽管全球各地仍在实施不同程度的出行限制措施，Automechanika Shanghai如期于2020年12月2至5日举行</text>
					</u-col>
				</u-row>
			</view>
		</view>
		<view class="past" v-if="current==1" @click="tozhanhui_De">
			<view class="changshang">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220502cs45.jpg" width="100%"
							height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>2022第十一届中国（上海）国际流体机械展览会</h3>
						<text class="u-line-3">中国国际流体机械展览会CFME于2001年创办，迄今已经成功举办了十届。纵观往届展览会，先后吸引了众多国内外***企业参加，诸如：美国通用电气(GE)、福斯(FLOWSERVE)、</text>
					</u-col>
				</u-row>
			</view>
			<view class="changshang">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220503cs46.jpg" width="100%"
							height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>2022中国(广州)国际医疗器械展览</h3>
						<text class="u-line-3">1、医用影像设备：CT、DR、医用X射线系统、超声诊断仪、磁共振设备、医用胶片及处理系统等；2、检验医学及实验室诊断设备：临床化学分析/诊断系统、临床医学检验辅助设备、实验器具类、整体实验室解决方案、家用诊断设备生化及自动生化分析仪等；</text>
					</u-col>
				</u-row>
			</view>
			<view class="changshang">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220503cs45.jpg" width="100%"
							height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>2022华南广州口腔设备及材料展会、2022广州数字化口腔展会</h3>
						<text class="u-line-3">1.	口腔材料 :牙科医疗材料及工具、前后牙通用充填材料、各种牙体材料、颌面外科专用器械及材料、牙体牙髓专用器械及材料、牙周病科专用器械及材料、正畸专用器械及材料、种植专用器械及材料、义齿修复材料和种植产品、其他用于牙科技工室诊所的附件和辅助材料等</text>
					</u-col>
				</u-row>
			</view>
			<view class="changshang">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220503cs44.jpg" width="100%"
							height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>2022第九届中国国际养老服务业博览会</h3>
						<text class="u-line-3">第九届中国国际养老服务业博览会将于2022年11月28-30日在北京国家会议中心举办。中国国际养老服务业博览会已成功举办八届，在民政部、全国老龄工作委员会办公室的关怀指导下，在国际社会和全社会的积极参与下，博览会已成促进国内外养老服务界快速融合的品牌展会。</text>
					</u-col>
				</u-row>
			</view>
			<view class="changshang">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220503cs43.jpg" width="100%"
							height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>2022深圳亚太口腔医学高新技术博览会</h3>
						<text class="u-line-3">国际品牌展区境外口腔企业； 国际知名大品牌企业； 拥有国际竞争力、国际优势高新技术展区口腔医疗器械、设备等企业；国家高新技术企业；口腔产品具有国际竞争力民族品牌展区民族品牌口腔企业；拥有自主创新知识产权、器械</text>
					</u-col>
				</u-row>
			</view>
			<view class="changshang">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_zhizao/file_20220503cs41.jpg" width="100%"
							height="200rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>2022第二十届上海国际车用空调及冷藏技术展览会</h3>
						<text class="u-line-3">伴随中国汽车产业的快速腾飞，我国移动制冷行业呈现快速发展趋势，从生产、销售到售后的各个环节都日渐成熟，同时，国家对行业产品低碳、 环保的要求不断提高，加速了企业产品创新及产业升级，市场潜力的巨大更是毋庸置疑。</text>
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
				current:0,
				list:[
					{
						name:'最新展会'
					},
					{
						name:'过往展会'
					}
				]
			}
		},
		methods: {
			changetab(index){
				this.current=index
			},
			tozhanhui_De(){
				uni.navigateTo({
					url:'zhanhui_details?state='+this.current
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
