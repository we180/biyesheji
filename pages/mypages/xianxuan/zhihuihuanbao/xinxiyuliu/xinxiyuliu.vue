<template>
	<view>
		<u-section title="请填写上门信息" font-size="40" :right="false"></u-section>
		<view class="">
			<u-field label="姓名" v-model="name"></u-field>
			<u-field label="电话" v-model="phone"></u-field>
			<u-field label="地址" v-model="address"></u-field>
			<u-field label="详细信息" v-model="details" type="textarea" style="height: 200rpx;"></u-field>
			<u-field label="备注" v-model="content" type="textarea"></u-field>
		</view>
		<view class="">
			<u-button type="success" @click="tijiao">提交</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				name:'',
				phone:'',
				address:'',
				details:'',
				content:''
			}
		},
		methods: {
			tijiao(){
				this.$u.toast('提交成功')
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
