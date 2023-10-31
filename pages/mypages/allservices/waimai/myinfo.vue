<template>
	<view>
		<view class="userimg">
			<image :src="baseUrl+'/prod-api'+userimg.avatar" mode=""></image>
			<h2>{{userimg.nickName}}</h2>
		</view>
		<view class="enter">
			<u-cell-group>
				<u-cell-item icon="integral-fill" title="地址管理" value="进入" @click="tochangeaddress"></u-cell-item>
				<u-cell-item icon="integral-fill" title="我的收藏" value="进入" @click="tomylike"></u-cell-item>
				<u-cell-item icon="integral-fill" title="我的订单" value="进入" @click="todingdan"></u-cell-item>
			</u-cell-group>
		</view>
		<view class="exit">
			<u-button type="error" @click="tologin">退出</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userimg:''
			}
		},
		methods: {
			todingdan(){
				uni.navigateTo({
					url:'orderlist'
				})
			},
			tologin(){
				uni.reLaunch({
					url:'../login/login'
				})
			},
			tomylike(){
				uni.navigateTo({
					url:'mylike'
				})
			},
			tochangeaddress(){
				uni.navigateTo({
					url:'change_address'
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/common/user/getInfo')
				this.userimg=res1.user
				console.log(res1);
			}
		},
		onLoad() {
			if(this.vuex_token==''){
				uni.redirectTo({
					url:'../login/login'
				})
			}else{
				this.getData()
			}
			
		}
		
	}
</script>

<style scoped>
	.userimg{
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	.userimg image{
		width: 300rpx;
		height: 300rpx;
		border-radius: 50%;
	}
</style>
