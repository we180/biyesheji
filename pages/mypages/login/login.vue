<template>
	<view>
		<u-field label="用户名" v-model="username"></u-field>
		<u-field label="密码" v-model="password" type="password"></u-field>
		<u-button type="success" @click="login">登录</u-button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				username:'',
				password:''
			}
		},
		methods: {
			login(){
				this.$u.post('/prod-api/api/login',{
					username:this.username,
					password:this.password
				}).then(res=>{
					console.log(res);
					this.$u.vuex('vuex_token',res.token)
					uni.switchTab({
						url:'../main/main'
					})
				})
			}
		}
	}
</script>

<style scoped>

</style>
