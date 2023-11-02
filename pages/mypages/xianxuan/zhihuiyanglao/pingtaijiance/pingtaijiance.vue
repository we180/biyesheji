<template>
	<view>
		<view class="head">
			<u-section :font-size="40" title="选择成员" sub-title="新增成员"></u-section>
			<view class="human">
				<u-row>
					<u-col span="3">
						<u-image src="../../../../../static/myimgs/myimg_yanglao/pionner2.png" width="100%" height="200rpx" mode="aspectFit"></u-image>
					</u-col>
					<u-col span="7">
						<view class="text" style="display: flex;flex-direction: column;">
							<h2>小红</h2>
							<text>性别:女</text>
							<text>年龄:51</text>
						</view>
					</u-col>
					<u-col span="2">
						<u-button type="warning">删除</u-button>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<u-section :font-size="40" title="健康状况" :right="false"></u-section>
			<!-- 心率、血压、体温、运动量、户外活动时间、体重 -->
			<u-field label="心率" v-model="xinlv" input-align="right" :disabled="true"></u-field>
			<u-field label="血压" v-model="xueya" input-align="right" :disabled="true"></u-field>
			<u-field label="体温" v-model="tiwen" input-align="right" :disabled="true"></u-field>
			<u-field label="运动量" v-model="yundong" input-align="right" :disabled="true"></u-field>
			<u-field label="户外活动时间" v-model="huodong" input-align="right" :disabled="true"></u-field>
			<u-field label="体重" v-model="tizhong" input-align="right" :disabled="true"></u-field>
			<u-gap></u-gap>
			<u-section :font-size="40" title="环境信息" :right="false"></u-section>
			<u-field label="温度" v-model="wendu" input-align="right" :disabled="true"></u-field>
			<u-field label="湿度" v-model="shidu" input-align="right" :disabled="true"></u-field>
			<u-field label="二氧化碳浓度" v-model="co2" input-align="right" :disabled="true"></u-field>
			<u-field label="PM2.5" v-model="pm25" input-align="right" :disabled="true"></u-field>
			<view class="u-tips-color u-m-20">
				更新时间:2022.12.9
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				xinlv:'81bmp',
				xueya:'95mmHg',
				tiwen:'36.4°C',
				yundong:'3785步',
				huodong:'2h/天',
				tizhong:'55kg',
				wendu:'24°C',
				shidu:'75%',
				co2:'10',
				pm25:'20dg/m³'
			}
		},
		methods: {
			
		}
	}
</script>

<style scoped>
	.human{
		margin: 10rpx;
		padding: 10rpx;
		border: #A0CFFF 4rpx solid;
		border-radius: 20rpx;
	}
</style>
