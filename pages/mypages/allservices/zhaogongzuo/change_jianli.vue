<template>
	<view>
		<view class="input">
			<u-field label="工作经验" v-model="experience"></u-field>
			<u-field label="最高学历" v-model="mostEducation"></u-field>
			<u-field label="现居住地" v-model="address"></u-field>
			<u-field label="期望职位" v-model="positionId"></u-field>
			<u-field label="期望薪资" v-model="money"></u-field>
			<u-field label="教育经历" v-model="education"></u-field>
			<u-field label="个人简介" v-model="individualResume"></u-field>
			<u-button type="success" @click="change" v-if="state==0">修改</u-button>
			<u-button type="success" @click="newjianli" v-if="state==1">新增</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				experience:'',
				mostEducation:'',
				address:'',
				positionId:'',
				money:'',
				education:'',
				individualResume:'',
				state:''
			}
		},
		methods: {
			newjianli(){
				this.$u.post('/prod-api/api/job/resume',{
					experience:this.experience,
					mostEducation:this.mostEducation,
					address:this.address,
					positionId:this.positionId,
					money:this.money,
					education:this.education,
					individualResume:this.individualResume
				}).then(res=>{
					console.log(res);
					this.$u.toast('新增成功')
				})
			},
			change(){
				this.$u.put('/prod-api/api/job/resume',{
					experience:this.experience,
					mostEducation:this.mostEducation,
					address:this.address,
					positionId:this.positionId,
					money:this.money,
					education:this.education,
					individualResume:this.individualResume
				}).then(res=>{
					console.log(res);
					this.$u.toast('修改成功')
				})
			},
		},
		onLoad(ops) {
			
			this.state=ops.state
			if(this.state==0){
				this.experience=ops.experience
				this.mostEducation=ops.mostEducation
				this.address=ops.address
				this.positionId=ops.positionId
				this.money=ops.money
				this.education=ops.education
				this.individualResume=ops.individualResume
			}
		}
	}
</script>

<style scoped>

</style>
