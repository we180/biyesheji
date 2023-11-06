<template>
	<view>
		<view class="head">
			<u-navbar title="学习心得">
				<u-icon name="order" color="#2979ff" size="50" label="学习历史" slot="right" style="margin-right: 20rpx;" @click="toxuexi_history"></u-icon> 
			</u-navbar> 
		</view>
		<view class="biji_list">
			<u-section title="学习笔记" font-size="40"></u-section>
			<view class="biji">
				<h3>最美志愿者 弘扬时代先锋</h3>
				<text class="u-line-4">
					2月5日是国际志愿者日，为了弘扬志愿服务精神。綦江区古南街道对24名最美志愿者进行了表彰。
					“虽然上年纪了，但是还是可以在社区发挥余热嘛，做一些力所能及的事情，也希望大家都参与到我们的志愿服务活动中来。”张丽萍老人接过奖状激动地说了自己的获奖感言。
				</text>
			</view>
			<view class="biji">
				<h3>脚踏实地 践行职责</h3>
				<text class="u-line-4">
					今年52岁的冯刚，是重庆市巫山县水行政执法支队副支队长，中共党员。2020年2月派驻双龙镇驻镇，2021年5月又派驻到骡坪镇凤岭村担任第一书记兼驻村工作队队长。
				</text>
			</view>
		</view>
		<view class="ganyan_list">
			<u-section title="学习感言" font-size="40"></u-section>
			<view class="ganyan">
				<h3>钢铁意志 人民英雄</h3>
				<text class="u-line-4">
					麦贤得，广东潮汕人，1945年出生于广东省潮州市饶平县汫洲镇一个船民家庭。  1964年3月参加中国人民解放军。1965年8月加入中国共产党。入伍后到广东虎门沙角海军联合学校学习。毕业后，被分配到海军护卫艇第41大队4中队611号护卫艇上，当了一名机电兵。 
				</text>
			</view>
			<view class="ganyan">
				<h3>优秀党员 道德模范</h3>
				<text class="u-line-4">
					包起帆，男，汉族，1951年2月出生，中共党员，浙江镇海人，工学硕士。 曾任上海港务局副局长、上海国际港务（集团）股份有限公司副总裁，上海市人民政府参事。现任华东师范大学国际航运物流研究院院长、教授。  他研发新型抓斗及工艺系统，推进港口装卸机械化，被誉为“抓斗大王”。参与开辟上海港首条内贸标准集装箱航线，建设我国首座集装箱自动化无人堆场，积极推进我国首套散矿装卸设备系统的研发，领衔制定集装箱—RFID货运标签系统国际标准。 包起帆带领团队技术创新，获国家发明奖3项、国家科学技术进步奖3项。九次荣获上海市劳动模范，连续五届荣获“全国劳动模范”，两次获得全国“五一”劳动奖章，被评为全国优秀共产党员、全国道德模范，入选“100位新中国成立以来感动中国人物”，2018年被授予“改革先锋”称号。 2019年9月25日，入选“最美奋斗者”个人名单。 
				</text>
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
			toxuexi_history(){
				uni.navigateTo({
					url:'xuexi_history'
				})
			},
		}
	}
</script>

<style scoped>
	.biji{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #ccc;
		border-radius: 20rpx;
	}
	.ganyan{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #ccc;
		border-radius: 20rpx;
	}
</style>
