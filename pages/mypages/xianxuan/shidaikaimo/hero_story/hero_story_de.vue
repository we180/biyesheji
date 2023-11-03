<template>
	<view>
		<view class="info">
			<u-section title="英雄事迹介绍" :right="false" font-size="40"></u-section>
			<view class="infotext">
				<text>[28] 9月17日13时30分许，神舟十二号载人飞船返回舱安全降落在东风着陆场预定区域。 [30-31]
					2021年11月23日，中共中央、国务院、中央军委给聂海胜颁发“一级航天功勋奖章”</text>
			</view>
		</view>
		<view class="zhijing">
			<u-button type="success" @click="zhijing"><text style="font-size: 40rpx;">致敬</text></u-button>
		</view>
		<u-gap></u-gap>
		<view class="pinlun">
			<u-section title="评论一下" :right="false" font-size="40"></u-section>
			<u-gap></u-gap>
			<view class="pinlun_in">
				<u-input type="textarea" style="height: 220rpx;" border="border" v-model="content"></u-input>
				<u-button type="success" @click="pinlun">发表评论</u-button>
			</view>
		</view>
		<u-gap></u-gap>
		<view class="storyall">
			<u-section title="英雄事迹文章" :right="false" font-size="40"></u-section>
			<view class="stroytext">
				<text>
					聂海胜，男，汉族，籍贯湖北枣阳，中共党员，博士学位。1964年9月出生，1983年6月于空军长春飞行学院入伍，1986年12月加入中国共产党。曾任空军航空兵某师某团司令部领航主任，安全飞行1480小时，被评为空军一级飞行员。现为中国人民解放军航天员大队特级航天员、中国航天员大队大队长、专业技术少将军衔。
					[13]
					1998年1月入选为我国首批航天员。2003年9月，入选神舟五号飞行任务备份航天员。2005年10月，执行神舟六号飞行任务，同年11月被中共中央、国务院、中央军委授予“英雄航天员”荣誉称号，并获“航天功勋奖章”。2008年5月，入选神舟七号飞行任务备份航天员。2012年3月，入选神舟九号飞行任务备份航天员。2013年6月，执行神舟十号飞行任务，担任指令长，同年7月，被中共中央、国务院、中央军委授予“二级航天功勋奖章”。2014年6月任中国人民解放军航天员大队大队长。2019年12月入选神舟十二号飞行任务乘组，担任指令长。
					[12] 2021年6月，执行神舟十二号飞行任务，担任指令长。 [17-18] 6月17日18时48分，航天员聂海胜进入天和核心舱，标志着中国人首次进入自己的空间站。 [21]
					8月20日，航天员聂海胜第二次出舱活动取得圆满成功。 [25] 2021年6月17日起，聂海胜执行神舟十二号载人飞行任务截至北京时间9月6日，聂海胜成为首位在轨100天的中国航天员。 [28]
					9月17日13时30分许，神舟十二号载人飞船返回舱安全降落在东风着陆场预定区域。 [30-31] 2021年11月23日，中共中央、国务院、中央军委给聂海胜颁发“一级航天功勋奖章”
				</text>
			</view>

		</view>
		<view class="video">
			<u-section title="英雄事迹视频" :right="false" font-size="40"></u-section>
			<u-gap></u-gap>
			<video src="../../../../../static/myimgs/myimg_kaimo/video03.mp4" controls style="width: 100%;"></video>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				content: ''
			}
		},
		methods: {
			zhijing() {
				this.$u.toast('致敬成功')
			},
			pinlun() {
				this.$u.toast('评论成功')
				this.content = ''
			},
		}
	}
</script>

<style scoped>
	.infotext {
		margin: 10rpx;
		padding: 10rpx;
		border: solid 2rpx #CCC;
		border-radius: 20rpx;
	}

	.stroytext {
		margin: 10rpx;
		padding: 10rpx;
		border: solid 2rpx #CCC;
		border-radius: 20rpx;
	}
</style>
