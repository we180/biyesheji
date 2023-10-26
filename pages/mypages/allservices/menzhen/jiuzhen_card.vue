<template>
	<view>
		<view class="add_card">
			<image src="../../../../static/uview/example/min_button_select.png" mode="" @click="addcard"></image>
		</view>
		<view class="cardall">
			<view class="cardlist" v-for="(item,cardlistid) in cardlist" :key="cardlistid">
				<view class="card">
					<span>姓名:{{item.name}}</span>
					<span>性别:{{item.sex}}</span>
					<span>身份证号:{{item.cardId}}</span>
					<span>出生日期:{{item.birthday||'未设置'}}</span>
					<span>手机号:{{item.tel}}</span>
					<span>地址:{{item.address}}</span>
				</view>
				<view class="card_to">
					<u-icon name="arrow-right-double" size="140" @click="tokeshi"></u-icon>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				cardlist: []
			}
		},
		methods: {
			tokeshi(){
				uni.navigateTo({
					url:'/pages/mypages/allservices/menzhen/keshifenzhen'
				})
			},
			addcard() {
				uni.navigateTo({
					url: '/pages/mypages/allservices/menzhen/card_index'
				})
			},
			async getData() {
				let res1 = await this.$u.get('/prod-api/api/hospital/patient/list')
				this.cardlist = res1.rows
				console.log(this.cardlist);
			}
		},
		onShow() {
			this.getData()
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.add_card {
		position: fixed;
		bottom: 0rpx;
		right: 39.5%;
	}

	.add_card image {
		width: 150rpx;
		height: 150rpx;
	}
	.cardlist{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: solid 4rpx pink;
		box-shadow: 8rpx 8rpx 16rpx skyblue;
		background-color: aliceblue;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}
	.card{
		display: flex;
		flex-direction: column;
	}
	.card>*{
		margin: 4rpx;
	}
	.card_to{
		display: flex;
		opacity: 0.5;
	}
</style>
