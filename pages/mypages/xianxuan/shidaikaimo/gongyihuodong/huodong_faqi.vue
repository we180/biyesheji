<template>
	<view>
		<u-field label="活动标题" v-model="title"></u-field>
		<u-field label="发起人" v-model="name"></u-field>
		<u-field label="活动简介" v-model="details" style="height: 400rpx;"></u-field>
		<u-button type="success" @click="huodongfaqi">活动发起</u-button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title:'',
				name:'',
				details:''
			}
		},
		methods: {
			huodongfaqi(){
				this.title=''
				this.name=''
				this.details=''
				this.$u.toast('发起成功')
				setTimeout(()=>{
					uni.navigateBack({
						delta:1
					})
				},500)
			}
		}
	}
</script>

<style scoped>

</style>
