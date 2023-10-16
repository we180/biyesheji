<template>
	<view>
		<view class="input">
			<u-field label="标题" v-model="title" maxlength="30" ></u-field>
			<u-field label="内容" v-model="content" maxlength="150" style="height: 300rpx;"></u-field>
			<u-button type="success" @click="submit">提交</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title:'',
				content:''
			}
		},
		methods: {
			submit(){
				this.title=''
				this.content=''
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
