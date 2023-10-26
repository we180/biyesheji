<template>
	<view>
		<view class="input">
			<u-field label="家庭住址" v-model="address"></u-field>
			<u-field label="出生日期" v-model="birthday" @click="showtime=true" :disabled="true"></u-field>
			<u-picker mode="time" v-model="showtime" @confirm="choosetime"></u-picker>
			<u-field label="身份证" v-model="cardId"></u-field>
			<u-field label="姓名" v-model="name"></u-field>
			<u-field label="性别" v-model="sex" @click="showsex=true" :disabled="true"></u-field>
			<u-action-sheet :list="sexlist" v-model="showsex" @click="choosex"></u-action-sheet>
			<u-field label="电话" v-model="tel"></u-field>
		</view>
		<u-gap></u-gap>
		<u-button type="success" @click="save">确定</u-button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				address:'',
				birthday:'',
				cardId:'',
				name:'',
				sex:'',
				tel:'',
				showtime:false,
				showsex:false,
				sexlist:[
					{
						text:'男'
					},
					{
						text:'女'
					}
				]
			}
		},
		methods: {
			choosetime(index){
				this.birthday=index.year+'-'+index.month+'-'+index.day
				console.log(index);
			},
			choosex(index){
				if (index==0) {
					this.sex='男'
				} else{
					this.sex='女'
				}
			},
			save(){
				this.$u.post('/prod-api/api/hospital/patient',{
					address:this.address,
					birthday:this.birthday,
					cardId:this.cardId,
					name:this.name,
					sex:this.sex,
					tel:this.tel
				}).then((res)=>{
					console.log(res);
					this.$u.toast('保存成功')
					uni.navigateBack({
						delta:1
					})
				})
			}
		}
		
	}
</script>

<style scoped>

</style>
