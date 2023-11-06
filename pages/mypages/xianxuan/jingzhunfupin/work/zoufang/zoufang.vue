<template>
	<view>
		<view class="huzhulist">
			<view class="huzhu">
				<h2>汝南县板店乡</h2>
				<h3>王明华</h3>
				<u-button type="success" @click="show=true">走访</u-button>
			</view>
			<view class="huzhu">
				<h2>玉门市独山子乡金旺村</h2>
				<h3>李晓红</h3>
				<u-button type="success" @click="show=true">走访</u-button>
			</view>
			<view class="huzhu">
				<h2>木林坪社区</h2>
				<h3>张伟</h3>
				<u-button type="success" @click="show=true">走访</u-button>
			</view>
			<view class="huzhu">
				<h2>临夏县尹集镇大滩村</h2>
				<h3>王娟</h3>
				<u-button type="success" @click="show=true">走访</u-button>
			</view>
			<view class="huzhu">
				<h2>兴山县榛子乡育林村</h2>
				<h3>张涛</h3>
				<u-button type="success" @click="show=true">走访</u-button>
			</view>
			<view class="huzhu">
				<h2>五峰县湾潭镇三台坡村</h2>
				<h3>李娜</h3>
				<u-button type="success" @click="show=true">走访</u-button>
			</view>
		</view>
		<u-popup mode="bottom" v-model="show">
			<u-field label="开始时间" v-model="start"></u-field>
			<u-field label="结束时间" v-model="end"></u-field>
			<u-field label="走访目的" v-model="content" type="textarea" style="height: 200rpx;"></u-field>
			<u-button type="primary" @click="tijiao">提交</u-button>
		</u-popup>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				show: false,
				start: '',
				end: '',
				content: '',

			}
		},
		methods: {
			tijiao() {
				this.$u.toast('提交申请成功!')
				this.start = ''
				this.end = ''
				this.content = ''
				this.show = false
			},
		}
	}
</script>

<style scoped>
	.huzhu {
		margin: 10rpx;
		padding: 10rpx;
		border: #ccc 4rpx solid;
		border-radius: 20rpx;
	}
	.huzhu>*{
		margin: 10rpx;
	}
</style>
