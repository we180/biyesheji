<template>
	<view>
		<view class="input">
			<!-- 公司名称、运单号、投诉类别和投诉内容 -->
			<u-field label="公司名称(ID)" v-model="name"></u-field>
			<u-field label="运单号" v-model="infono"></u-field>
			<u-field label="投诉类别" v-model="type" :disabled="true"></u-field>
			<u-field label="投诉内容" v-model="content" style="height: 200rpx;"></u-field>
			<u-button type="success" @click="queren">确认</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				name:'',
				infono:'',
				type:'1',
				content:''
			}
		},
		methods: {
			queren(){
				this.$u.post('/prod-api/api/logistics-inquiry/logistics_complaint',{
					companyId:this.name,
					infoNo:this.infono,
					questionType:this.type,
					description:this.content
				}).then(res=>{
					console.log(res);
					this.$u.toast('提交成功')
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
