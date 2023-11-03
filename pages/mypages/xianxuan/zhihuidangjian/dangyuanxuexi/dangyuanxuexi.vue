<template>
	<view>
		<view class="head">
			<u-dropdown>
				<u-dropdown-item title="课程分类" :options="options1"></u-dropdown-item>
				<u-dropdown-item title="章节管理" :options="options2"></u-dropdown-item>
			</u-dropdown>
		</view>
		<u-gap></u-gap>
		<view class="" @click="toxuexi_De">
			<u-row>
				<u-col span="4">
					<image src="../../../../../static/myimgs/myimg_dangjian/banner1.png" mode="" style="width: 230rpx; height: 230rpx;"></image>
				</u-col>
				<u-col span="8">
					<h3>山东城市建设职业学院智慧党建应用</h3>
					<text>学习进度:<u-line-progress :percent="70" :show-percent="true"></u-line-progress> </text>
				</u-col>
			</u-row>
			<u-gap></u-gap>
			<u-row>
				<u-col span="4">
					<image src="../../../../../static/myimgs/myimg_dangjian/1.jpg" mode="" style="width: 230rpx; height: 230rpx;"></image>
				</u-col>
				<u-col span="8">
					<h3>塔里木油田：智慧党建激发活力</h3>
					<text>学习进度:<u-line-progress :percent="40" :show-percent="true"></u-line-progress> </text>
				</u-col>
			</u-row>
			<u-gap></u-gap>
			<u-row>
				<u-col span="4">
					<image src="../../../../../static/myimgs/myimg_dangjian/2.jpg" mode="" style="width: 230rpx; height: 230rpx;"></image>
				</u-col>
				<u-col span="8">
					<h3>中国石油天然气集团有限公司党建信息化平台</h3>
					<text>学习进度:<u-line-progress :percent="90" :show-percent="true"></u-line-progress> </text>
				</u-col>
			</u-row>
			<u-gap></u-gap>
			<u-row>
				<u-col span="4">
					<image src="../../../../../static/myimgs/myimg_dangjian/3.jpg" mode="" style="width: 230rpx; height: 230rpx;"></image>
				</u-col>
				<u-col span="8">
					<h3>江西铜业集团有限公司党建信息化平台一期建设项目</h3>
					<text>学习进度:<u-line-progress :percent="89" :show-percent="true"></u-line-progress> </text>
				</u-col>
			</u-row>
			<u-gap></u-gap>
			<u-row>
				<u-col span="4">
					<image src="../../../../../static/myimgs/myimg_dangjian/4.jpg" mode="" style="width: 230rpx; height: 230rpx;"></image>
				</u-col>
				<u-col span="8">
					<h3>山东城市建设职业学院智慧党建应用</h3>
					<text>学习进度:<u-line-progress :percent="55" :show-percent="true"></u-line-progress> </text>
				</u-col>
			</u-row>
			<u-gap></u-gap>
			<u-row>
				<u-col span="4">
					<image src="../../../../../static/myimgs/myimg_dangjian/5.jpg" mode="" style="width: 230rpx; height: 230rpx;"></image>
				</u-col>
				<u-col span="8">
					<h3>中国邮政集团公司党建信息化平台</h3>
					<text>学习进度:<u-line-progress :percent="60" :show-percent="true"></u-line-progress> </text>
				</u-col>
			</u-row>
			<u-gap></u-gap>
			<u-row>
				<u-col span="4">
					<image src="../../../../../static/myimgs/myimg_dangjian/6.jpg" mode="" style="width: 230rpx; height: 230rpx;"></image>
				</u-col>
				<u-col span="8">
					<h3>中国物流股份有限公司党建云</h3>
					<text>学习进度:<u-line-progress :percent="76" :show-percent="true"></u-line-progress> </text>
				</u-col>
			</u-row>
			<u-gap></u-gap>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				options1: [{
						label: '分类1'
					},
					{
						label: '分类2'
					}
				],
				options2: [{
						label: '章节1'
					},
					{
						label: '章节2'
					}
				],
			}
		},
		methods: {
			toxuexi_De(){
				uni.navigateTo({
					url:'xuexi_de'
				})
			},
		}
	}
</script>

<style>

</style>
