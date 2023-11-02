<template>
	<view class="u-m-20">
		<view class="input">
			<h3>评价一下</h3>
			<u-gap></u-gap>
			<u-input type="textarea" border="border" v-model="content"></u-input>
			<u-gap></u-gap>
			<u-button type="success" @click="uppingjia">提交评价</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				content:''
			}
		},
		methods: {
			uppingjia(){
				this.$u.toast('评价成功')
				this.content=''
				setTimeout(()=>{
					uni.navigateBack({
						delta:1
					})
				},700)
			},
		}
	}
</script>

<style>

</style>
