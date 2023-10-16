<template>
	<view>
		<view class="input">
			<u-field label="原密码" v-model="oldpwd"></u-field>
			<u-field label="新密码" v-model="newpwd"></u-field>
			<u-button type="success" @click="changepwd">确定</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				oldpwd:'',
				newpwd:''
			}
		},
		methods: {
			changepwd(){
				this.$u.put('/prod-api/api/common/user/resetPwd',{
					oldPassword:this.oldpwd,
					newPassword:this.newpwd
				}).then(res=>{
					console.log(res);
					this.$u.toast('修改成功')
					setTimeout(()=>{
						uni.navigateBack({
							delta:1
						})
					},700)
				})
			},
		}
	}
</script>

<style scoped>

</style>
