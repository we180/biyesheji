<template>
	<view>
		<view class="input">
			<u-field label="入场时间" v-model="entertime" placeholder="yyyy-mm-dd 00:00:00"></u-field>
			<u-field label="出场时间" v-model="exittime" placeholder="yyyy-mm-dd 00:00:00"></u-field>
			<u-button type="primary" @click="search">查询</u-button>
		</view>
		<view class="jilu_list">
<!-- 车牌号、收费金额、入场时间、出场时间、停车场名称。点击“查看更多”按钮可查看更多停车记录，默认显示5—6条停车记录。 -->
			<view class="jilu" v-for="(item,jilulistid) in jilulist.slice(0,size)" :key="jilulistid">
				<h3>{{item.plateNumber}}</h3>
				<text>收费金额:{{item.monetary}}元</text>
				<text>入场时间:{{item.entryTime}}</text>
				<text>出场时间:{{item.outTime}}</text>
				<text>停车场名称:{{item.parkName}}</text>
			</view>
			<u-button type="success" @click="lookmore">查看更多</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				jilulist:[],
				size:5,
				entertime:'',
				exittime:''
			}
		},
		methods: {
			search(){
				this.$u.get('/prod-api/api/park/lot/record/list?entryTime='+this.entertime+'&outTime='+this.exittime).then(res=>{
					this.jilulist=res.rows
					console.log(res);
				})
			},
			lookmore(){
				if(this.jilulist.length>this.size){
					this.size=this.size+5
				}else{
					this.$u.toast('没有更多了')
				}
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/park/lot/record/list')
				this.jilulist=res1.rows
				console.log(res1);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.jilu{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
		display: flex;
		flex-direction: column;
	}
</style>
