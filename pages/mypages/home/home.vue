<template>
	<view>
		<view class="user">
			<u-image width="300rpx" height="300rpx" :src="baseUrl+'/prod-api'+userinfo.avatar" border-radius="50%"></u-image>
			<h2>{{userinfo.nickName}}</h2>
		</view>
		<u-gap></u-gap>
		<view class="enter">
			<u-cell-group>
				<u-cell-item icon="integral-fill" title="个人信息" @click="touserinfo"></u-cell-item>
				<u-cell-item icon="integral-fill" title="订单列表" @click="todingdan"></u-cell-item>
				<u-cell-item icon="integral-fill" title="修改密码" @click="tochangepwd"></u-cell-item>
				<u-cell-item icon="integral-fill" title="意见反馈" @click="toadvise"></u-cell-item>
			</u-cell-group>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userinfo:''
			}
		},
		methods: {
			touserinfo(){
				uni.navigateTo({
					url:'userinfo'
				})
			},
			todingdan(){
				uni.navigateTo({
					url:'dingdan_list'
				})
			},
			tochangepwd(){
				uni.navigateTo({
					url:'changepwd'
				})
			},
			toadvise(){
				uni.navigateTo({
					url:'advise'
				})
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/common/user/getInfo')
				this.userinfo=res1.user
				// console.log(res1);
			}
		},
		onLoad() {
			this.getData()
		},
		onShow() {
			this.getData()
		},
	}
</script>

<style scoped>
	.user{
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
	}
</style>
