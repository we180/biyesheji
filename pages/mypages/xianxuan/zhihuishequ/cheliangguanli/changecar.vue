<template>
	<view>
		<view class="input">
			<!-- 车牌号码、车位号、停车卡号、车主姓名、车主手机号、相关住户姓名和地址 -->
			<u-field label="车牌号码" v-model="info.carnum"></u-field>
			<u-field label="车位号" v-model="info.stopnum"></u-field>
			<u-field label="停车卡号" v-model="info.stopcard"></u-field>
			<u-field label="车主姓名" v-model="info.carname"></u-field>
			<u-field label="车主手机号" v-model="info.carphone"></u-field>
			<u-field label="相关住户姓名" v-model="info.username"></u-field>
			<u-field label="地址" v-model="info.address"></u-field>
			<u-button type="success" @click="addcar">修改</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				info:{
					carnum:'',
					stopnum:'',
					stopcard:'',
					carname:'',
					carphone:'',
					username:'',
					address:'',
				}
			}
		},
		methods: {
			addcar(){
				let temp=this.shequcar_list
				temp[this.id]=JSON.parse(JSON.stringify(this.info))
				this.$u.vuex('shequcar_list',temp)
				this.$u.toast('添加成功')
				setTimeout(()=>{
					uni.navigateBack({
						delta:1
					})
				},700)
			},
		},
		onLoad(ops) {
			this.id=ops.id
			this.info=this.shequcar_list[this.id]
		}
	}
</script>

<style scoped>

</style>
