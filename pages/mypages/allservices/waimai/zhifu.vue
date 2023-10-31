<template>
	<view>
		<view class="">
			<h2 style="text-align: center;">需支付金额:{{total}}</h2>
			<u-gap></u-gap>
			<u-gap></u-gap>
			<u-gap></u-gap>
			<u-button type="success" @click="show=true">选择电子钱包支付类型</u-button>
			<u-action-sheet :list="list" @click="click" v-model="show"></u-action-sheet> 
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				show:false,
				total:'',
				list:[
					{
						text:'电子钱包'
					},
					{
						text:'微信'
					},
					{
						text:'支付宝'
					}
				],
				orderNo:''
			}
		},
		methods: {
			click(index){
				this.$u.post('/prod-api/api/takeout/pay',{
					orderNo:this.orderNo,
					paymentType:this.list[index].text
				}).then(res=>{
					console.log(res);
					this.$u.toast('支付成功')
					setTimeout(()=>{
						uni.switchTab({
							url:'waimai'
						})
					},700)
				})
				console.log(this.list[index].text);
				
			}
		},
		onLoad(ops) {
			this.total=ops.total
			this.orderNo=ops.orderNo
		}
	}
</script>

<style scoped>

</style>
