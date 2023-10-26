<template>
	<view>
		<view class="input">
			<u-field label="科室分类编号" v-model="categoryId" labelWidth="200"></u-field>
			<u-field label="金额" v-model="money"></u-field>
			<u-field label="患者姓名" v-model="patientName"></u-field>
			<u-field label="预约时间" v-model="reserveTime" @click="showtime=true" :disabled="true"></u-field>
			<u-picker mode="time" v-model="showtime" @confirm="choosetime" :params="params"></u-picker>
			<u-field label="门诊类型" v-model="type" :disabled="true"></u-field>
		</view>
		<u-button type="success" @click="yuyue">预约</u-button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showtime: false,
				categoryId: '',
				money: '',
				type: '1',
				patientName: '',
				reserveTime: '',
				params: {
					year: true,
					month: true,
					day: true,
					hour: true,
					minute: true,
					second: false
				},
			}
		},
		methods: {
			choosetime(index) {
				this.reserveTime = index.year + '-' + index.month + '-' + index.day+' '+index.hour+':'+index.minute
				console.log(index);
			},
			yuyue() {
				// this.$u.toast('预约成功')
				this.$u.post('/prod-api/api/hospital', {
					categoryId: this.categoryId,
					money: this.money,
					patientName: this.patientName,
					reserveTime: this.reserveTime,
					type: this.type
				}).then((res) => {
					this.$u.toast('预约成功')
				})
			}
		}
	}
</script>

<style scoped>

</style>
