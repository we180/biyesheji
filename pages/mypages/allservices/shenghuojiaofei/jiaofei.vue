<template>
	<view>
		<view class="infoall">
			<u-row>
				<u-col span="8">
					<h3>交费项目:话费充值</h3>
					<h3>交费手机号:{{phone}}</h3>
				</u-col>
				<u-col span="4">
					<u-icon name="plus-circle" color="#2979ff" size="60" label="添加常用手机号" label-size="40" @click="addphone"></u-icon> 
				</u-col>
			</u-row>
			
		</view>
		<u-gap></u-gap>
		<view class="icon">
			<u-icon name="rmb" color="#2979ff" size="106" label="50元" label-pos="bottom" label-size="44" @click="money1"></u-icon>
			<u-icon name="rmb" color="#2979ff" size="106" label="100元" label-pos="bottom" label-size="44" @click="money2"></u-icon>
			<u-icon name="rmb" color="#2979ff" size="106" label="200元" label-pos="bottom" label-size="44" @click="money3"></u-icon>
			
		</view>
		<u-field label="支付金额(元)" v-model="money"></u-field>
		<u-gap></u-gap>
		<u-button type="success" @click="zhifu">去支付</u-button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				phone:'',
				money:''
			}
		},
		methods: {
			zhifu(){
				this.$u.post('/prod-api/api/living/phone/recharge',{
					paymentType:"电子支付",
					phonenumber:this.phone,
					rechargeAmount:this.money,
					ruleId:1,
					type:"2"
				}).then(res=>{
					console.log(res);
					this.money=''
				})
			},
			money1(){
				this.money='50'
			},
			money2(){
				this.money='100'
			},
			money3(){
				this.money='200'
			},
			addphone(){
				this.$u.toast('添加成功')
			},
		},
		onLoad(ops) {
			this.phone=ops.phone
		}
	}
</script>

<style scoped>
	.icon{
		display: flex;
		flex-direction: row;
		justify-content: space-around;
	}
	.info{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
