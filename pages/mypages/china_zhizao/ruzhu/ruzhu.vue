<template>
	<view>
		<view class="input">
			<u-field label="姓名" v-model="name"></u-field>
			<u-field label="公司名称" v-model="company"></u-field>
			<u-field label="联系电话" v-model="phone"></u-field>
			<u-field label="经营范围" v-model="area" style="height: 200rpx;"></u-field>
			<u-button type="success" @click="submit">提交</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				name:'',
				company:'',
				phone:'',
				area:''
			}
		},
		methods: {
			submit(){
				this.name=''
				this.company=''
				this.phone=''
				this.area=''
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
