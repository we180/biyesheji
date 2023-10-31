<template>
	<view>
		<u-field label="号牌种类" v-model="type"></u-field>
		<u-field label="车牌号码" v-model="carnum" @click="showcarnum=true"></u-field>
		<u-keyboard mode="car" v-model="showcarnum" @change="getcarnum"></u-keyboard>
		<u-field label="发动机号" v-model="enginenum"></u-field>
		<u-button type="primary" @click="search">查询</u-button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showcarnum:false,
				carnum:'',
				type:'',
				enginenum:''
			}
		},
		methods: {
			getcarnum(index){
				this.carnum+=index
			},
			search(){
				uni.navigateTo({
					url:'weizhang_list?type='+this.type+'&carnum='+this.carnum+'&enginenum='+this.enginenum
				})
			},
		}
	}
</script>

<style scoped>

</style>
