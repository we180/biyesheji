<template>
	<view>
		<swiper :indicator-dots="true" :interval="3000" :duration="1000">
			<swiper-item>
				<view class="swiper-item">
					<image src="../../../static/myimgs/guide1.jpg" mode=""></image>
				</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item">
					<image src="../../../static/myimgs/guide2.jpg" mode=""></image>
				</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item">
					<image src="../../../static/myimgs/guide3.jpg" mode=""></image>
				</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item">
					<image src="../../../static/myimgs/guide4.jpg" mode=""></image>
				</view>
			</swiper-item>
			<swiper-item>
				<view class="wangluo">
					<u-button type="primary" @click="showip=true">网络设置</u-button>
				</view>
				<view class="tologin">
					<u-button type="success" @click="tologin">进入主页</u-button>
					<u-popup v-model="showip" mode="center">
						<u-field label="IP地址" v-model="ip"></u-field>
						<u-field label="端口" v-model="port"></u-field>
						<u-button type="success" @click="saveip">确定</u-button>
					</u-popup>
				</view>
				<view class="swiper-item">
					<image src="../../../static/myimgs/guide5.jpg" mode=""></image>
				</view>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showip:false,
				ip:'',
				port:''
			}
		},
		methods: {
			tologin(){
				uni.redirectTo({
					url:'login'
				})
			},
			saveip(){
				this.$u.vuex('baseUrl','http://'+this.ip+':'+this.port)
				this.$u.toast('设置成功')
				this.showip=false
			},
		},
		onLoad() {
			const value=uni.getStorageSync('openflag')
			if(value){
				uni.redirectTo({
					url:'login'
				})
			}else{
				uni.setStorageSync('openflag',1)
			}
		}
		
	}
</script>

<style scoped>
	swiper{
		width: 100%;
		height: 100vh;
	}
	image{
		width: 100%;
		height: 100vh;
	}
	.tologin{
		position: fixed;
		bottom: 80rpx;
		right: 23%;
		width: 400rpx;
		z-index: 1;
	}
	.wangluo{
		position: fixed;
		top: 50rpx;
		right: 50rpx;
		width: 300rpx;
		z-index: 1;
	}
</style>
