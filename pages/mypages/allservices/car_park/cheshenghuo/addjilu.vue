<template>
	<view>
		<view class="head">
			<u-navbar title="添加加油记录">
				<u-icon @click="save" name="download" color="#2979ff" size="50" label="保存" label-size="36" slot="right" style="margin-right: 10rpx;"></u-icon> 
			</u-navbar> 
		</view>
		<view class="input">
			<!-- 录入信息包括：添加日期、里程、金额、油价、油量 -->
			<u-field label="添加日期"></u-field>
			<u-field label="里程"></u-field>
			<u-field label="金额"></u-field>
			<u-field label="油价"></u-field>
			<u-field label="油量"></u-field>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			save(){
				this.$u.toast('保存成功')
				setTimeout(()=>{
					uni.navigateBack({
						delta:1
					})
				},700)
			},
		}
	}
</script>

<style scoped>

</style>
