<template>
	<view>
		<view class="upload">
			<u-section title="上传身边的符合时代楷模的事迹" font-size="40" :right="false"></u-section>
			<u-gap></u-gap>
			<h3>具体事迹:</h3>
			<u-input type="textarea" style="height: 220rpx;" border="border"></u-input>
			<u-gap></u-gap>
			<h3>照片:</h3>
			<u-upload :action="action"></u-upload>
			<u-gap></u-gap>
<!-- 			<h3>视频:</h3>
			<view class="uploadvideo" @click="choosevideo">
				<video :src="baseUrl+'/prod-api'+videopath" controls style="width: 100%;"></video>
			</view> -->
			<u-button type="success" @click="submit">上传</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				action:"http://192.168.23.91:10001/prod-api/common/upload",
				// videopath:'',
				token:'eyJhbGciOiJIUzUxMiJ9.eyJsb2dpbl91c2VyX2tleSI6ImM4NDkyZDg2LTI0NDItNGFiYS04Y2MzLTI3ZDE0NmFkOTkzMyJ9.jubVwyiQDuUh3tPQn1vdl0gcHPUDaI81Zd8lu6KwSv-BFt_Qp7KVYzIO6xkLYRrpEotARDftoT26D1Hns01fZQ'
			}
		},
		methods: {
			submit(){
				uni.showToast({
					title: '上传成功'
				});
				setTimeout(()=>{
					uni.navigateBack({
						delta:1
					})
				},300)
			},
			// choosevideo(){
			// 	uni.chooseVideo({
			// 		sourceType:['album'],
			// 		success: (res) => {
			// 			var tempvideo=res.tempFilePaths
			// 			uni.uploadFile({
			// 				url:this.baseUrl+'/prod-api/common/upload',
			// 				filePath:tempvideo,
			// 				name:'file',
			// 				fileType:'video',
			// 				header:{
			// 					Authorization:this.token
			// 				},
			// 				success: (res) => {
			// 					console.log(res);
			// 					var value=JSON.parse(res.data)
			// 					this.videopath=value.fileName
			// 				}
			// 			})
			// 		}
			// 	})
			// }
		},
	}
</script>

<style scoped>
	.upload{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #ccc;
		border-radius: 20rpx;
	}
</style>
