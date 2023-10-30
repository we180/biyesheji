<template>
	<view>
		<!-- 标题、诉求内容、图片、承办单位、反馈手机号和发布按钮 -->
		<view class="choosetype" v-if="other==1">
			<u-field label="诉求分类" v-model="type" @click="showtype=true" :disabled="true"></u-field>
			<u-select v-model="showtype" :list="typelist" @confirm="choosetype"></u-select>
		</view>
		<view class="input">
			<u-field label="标题" v-model="title"></u-field>
			<u-field label="诉求内容" v-model="content"></u-field>
			<u-gap></u-gap>
			<view class="uploadimg">
				<u-section title="上传图片" :right="false" font-size="38"></u-section>
				<image :src="baseUrl+'/prod-api'+uploadimg" mode="" @click="showimg=true"></image>
				<u-action-sheet :list="imglist" v-model="showimg" @click="chooseimg"></u-action-sheet>
			</view>
			
			<u-field label="承办单位" v-model="undertaker"></u-field>
			<u-field label="反馈手机号" v-model="phone" label-width="150"></u-field>
			<u-button type="success" @click="fabu">发布</u-button>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				type:'',
				id:'',
				showimg:false,
				title:'',
				content:'',
				undertaker:'',
				phone:'',
				uploadimg:'',
				imglist:[
					{
						text:'相机'
					},
					{
						text:'相册'
					}
				],
				other:0,
				showtype:false,
				typelist:[]
			}
		},
		methods: {
			gettype(){
				if(this.other==1){
					this.$u.get('/prod-api/api/gov-service-hotline/appeal-category/list').then(res=>{
						res.rows.forEach(res=>{
							let label=res.name
							let value=res.id
							this.typelist.push({
								label,
								value
							})
						})
						console.log(this.typelist);
					})
				}
				else{
					
				}
			},
			choosetype(index){
				this.type=index[0].label
				this.id=index[0].value
			},
			fabu(){
				this.$u.post('/prod-api/api/gov-service-hotline/appeal',{
					"appealCategoryId": this.id,
					"title": this.title,
					"content": this.content,
					"undertaker": this.undertaker,
					"imgUrl": this.uploadimg
				}).then(res=>{
					console.log(res);
					this.title=''
					this.content=''
					this.undertaker=''
					this.uploadimg=''
					this.phone=''
				})
			},
			chooseimg(index) {
				if (index == 0) {
					uni.chooseImage({
						count: 1,
						sizeType: ['original'],
						sourceType: ['camera'],
						success: (res) => {
							var tempimg = res.tempFilePaths
							uni.uploadFile({
								url: this.baseUrl + '/prod-api/common/upload',
								filePath: tempimg[0],
								name: 'file',
								header: {
									Authorization: this.vuex_token
								},
								success: (res) => {
									var value = JSON.parse(res.data)
									this.uploadimg = value.fileName
								}
							})
						}
					})
				}else{
					uni.chooseImage({
						count: 1,
						sizeType: ['original'],
						sourceType:['album'],
						success: (res) => {
							var tempimg = res.tempFilePaths
							uni.uploadFile({
								url: this.baseUrl + '/prod-api/common/upload',
								filePath: tempimg[0],
								name: 'file',
								header: {
									Authorization: this.vuex_token
								},
								success: (res) => {
									var value = JSON.parse(res.data)
									this.uploadimg = value.fileName
								}
							})
						}
					})
				}
			},
		},
		onLoad(ops) {
			this.id=ops.id
			this.other=ops.other
			this.gettype()
		}
	}
</script>

<style scoped>
	
</style>
