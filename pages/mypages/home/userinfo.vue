<template>
	<view>
		<view class="userinfo">
			<view class="userimg" @click="showimg=true">
				<text>头像</text>
				<u-image width="120rpx" height="120rpx" :src="baseUrl+'/prod-api'+userinfo.avatar" border-radius="50%"></u-image>
				<u-action-sheet :list="imglist" @click="chooseimg" v-model="showimg"></u-action-sheet>
			</view>
			<view class="usertext">
				<u-field label="昵称" v-model="userinfo.nickName"></u-field>
				<u-field label="性别" v-model="userinfo.sex==0?'男':'女'" :disabled="true" @click="showsex=true"></u-field>
				<u-action-sheet :list="sexlist" @click="choosex" v-model="showsex"></u-action-sheet> 
				<u-field label="联系电话" v-model="limitphone" @focus="showphone" @blur="hidephone"></u-field>
			</view>
			<u-button type="success" @click="changeinfo">修改</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showimg:false,
				showsex:false,
				limitphone:'',
				userinfo:{
					avatar:'',
					nickName:'',
					sex:'',
					phonenumber:''
				},
				sexlist:[
					{
						text:'男'
					},
					{
						text:'女'
					}
				],
				imglist:[
					{
						text:'相机'
					},
					{
						text:'相册'
					}
				],
			}
		},
		methods: {
			showphone(){
				this.limitphone=this.userinfo.phonenumber
			},
			hidephone(){
				this.userinfo.phonenumber=this.limitphone
				this.limitphone=this.userinfo.phonenumber.substr(0,7)+'****'
			},
			changeinfo(){
				this.$u.put('/prod-api/api/common/user',{
					avatar:this.userinfo.avatar,
					nickName:this.userinfo.nickName,
					sex:this.userinfo.sex,
					phonenumber:this.userinfo.phonenumber
				}).then(res=>{
					console.log(res);
					this.$u.toast('修改成功')
				})
			},
			choosex(index){
				this.userinfo.sex=index
			},
			chooseimg(index){
				if(index==0){
					uni.chooseImage({
						count:1,
						sourceType:['camera'],
						success: (res) => {
							var tempimg=res.tempFilePaths
							uni.uploadFile({
								url:this.baseUrl+'/prod-api/common/upload',
								filePath:tempimg[0],
								name:'file',
								header:{
									Authorization:this.vuex_token
								},
								success:(res)=>{
									var value=JSON.parse(res.data)
									this.userinfo.avatar=value.fileName
								}
							})
						}
					})
				}else{
					uni.chooseImage({
						count:1,
						sourceType:['album'],
						success: (res) => {
							var tempimg=res.tempFilePaths
							uni.uploadFile({
								url:this.baseUrl+'/prod-api/common/upload',
								filePath:tempimg[0],
								name:'file',
								header:{
									Authorization:this.vuex_token
								},
								success:(res)=>{
									var value=JSON.parse(res.data)
									this.userinfo.avatar=value.fileName
								}
							})
						}
					})
				}
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/common/user/getInfo')
				// console.log(res1);
				this.userinfo=res1.user
				this.limitphone=this.userinfo.phonenumber.substr(0,7)+'****'
			},
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.userimg{
		display: flex;
		justify-content: space-between;
		margin-left: 28rpx;
		margin-right: 28rpx;
	}
	.userimg>*{
		display: flex;
		justify-content: center;
		align-items: center;
	}
</style>
