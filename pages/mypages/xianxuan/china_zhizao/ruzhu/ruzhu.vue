<template>
	<view>
		<!-- 厂商填写入驻申请信息表，供运营人员线下联系厂商。 -->
		<view class="input">
			<u-field label="姓名" v-model="name"></u-field>
			<u-field label="联系电话" v-model="phone"></u-field>
			<u-field label="公司名称" v-model="company" type="textarea"></u-field>
			<u-field label="经营范围" v-model="size" type="textarea" style="height: 200rpx;"></u-field>
			<u-button type="success" @click="submit">提交</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				name:'',
				phone:'',
				company:'',
				size:''
			}
		},
		methods: {
			submit(){
				this.$u.toast('提交成功')
				setTimeout(()=>{
					uni.redirectTo({
						url:'../china_zhizao'
					})
				},800)
			},
		}
	}
</script>

<style scoped>

</style>
