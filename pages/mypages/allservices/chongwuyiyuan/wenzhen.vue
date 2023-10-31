<template>
<!-- 页面显示医生头像、医生姓名、医生职称、执业编号、问题描述多文本输入框、图片和提交按钮，点击提交按钮时弹出提交结果提示，提交成功后跳转至主页面 -->
	<view>
		<view class="docinfo">
			<view class="img">
				<image :src="baseUrl+inf.avatar" mode=""></image>
			</view>
			<view class="text">
				<h3 style="text-align: center;">{{inf.name}}</h3>
				<text>医生职称:{{inf.jobName}}</text>
				<text>执业编号:{{inf.practiceNo}}</text>
			</view>
		</view>
		<view class="input">
			<h3 style="text-align: center;">问题描述</h3>
			<u-input border="border" height="300" type="textarea" placeholder="请输入问题" v-model="question"></u-input>
			<h3 style="text-align: center;">上传图片</h3>
			<image :src="baseUrl+'/prod-api'+imageUrls" mode="" @click="showimg=true"></image>
			<u-action-sheet :list="imglist" v-model="showimg" @click="chooseimg"></u-action-sheet>
			<u-button type="success" @click="upwenzhen">提交</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showimg:false,
				inf:{},
				question:'',
				imageUrls:'',
				imglist:[
					{
						text:'相机',
					},
					{
						text:'相册'
					}
				],
			}
		},
		methods: {
			chooseimg(index){
				if(index==0){
					uni.chooseImage({
						count:1,
						sizeType:['original'],
						sourceType:['camera'],
						success: (res) => {
							const tempimg=res.tempFilePaths
							uni.uploadFile({
								url:this.baseUrl+'/prod-api/common/upload',
								filePath:tempimg[0],
								name:'file',
								header:{
									Authorization:this.vuex_token
								},
								success: (res) => {
									var value=JSON.parse(res.data)
									this.imageUrls=value.fileName
								}
							})
						}
					})
				}else{
					uni.chooseImage({
						count:1,
						sizeType:['original'],
						sourceType:['album'],
						success: (res) => {
							const tempimg=res.tempFilePaths
							uni.uploadFile({
								url:this.baseUrl+'/prod-api/common/upload',
								filePath:tempimg[0],
								name:'file',
								header:{
									Authorization:this.vuex_token
								},
								success: (res) => {
									var value=JSON.parse(res.data)
									this.imageUrls=value.fileName
								}
							})
						}
					})
				}
				
			},
			upwenzhen(){
				this.$u.post('/prod-api/api/pet-hospital/inquiry',{
					doctorId:this.inf.id,
					question:this.question,
					imageUrls:this.imageUrls
				}).then((res)=>{
					console.log(res);
					this.$u.toast('提交成功')
					setTimeout(()=>{
						uni.switchTab({
							url:'chongwuyiyuan'
						})
					},700)
				})
			},
		},
		onLoad(options) {
			this.inf = JSON.parse(options.item)
			console.log(this.inf);
		}
	}
</script>

<style scoped>
	.text{
		display: flex;
		flex-direction: column;
	}
	.img image{
		width: 100%;
	}
	.input image{
		background-color: #ccc;
		width: 100%;
	}
</style>
