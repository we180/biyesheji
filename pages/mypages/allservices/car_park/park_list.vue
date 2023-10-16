<template>
	<view>
		<view class="input">
			<u-field label="入场时间" v-model="entertime" placeholder="xxxx-xx-xx 00:00:00"></u-field>
			<u-field label="出场时间" v-model="outtime" placeholder="xxxx-xx-xx 00:00:00"></u-field>
			<u-button type="success" @click="search">查询</u-button>
		</view>
		<!-- 车牌号、收费金额、入场时间、出场时间、停车场名称 -->
		<view class="carlist" v-for="(item,carlistid) in carlist" :key="carlistid">
			<h2>{{item.plateNumber}}</h2>
			<text>收费金额:{{item.monetary}}元</text>
			<text>入场时间:{{item.entryTime}}</text>
			<text>出场时间:{{item.outTime}}</text>
			<text>停车场名称:{{item.parkName}}</text>
		</view>
		<view class="lookmore">
			<u-button type="primary" @click="lookmore" v-if="showmore">查看更多</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showmore:false,
				entertime:'',
				outtime:'',
				total:0,
				pageNum:1,
				carlist:[]
			}
		},
		methods: {
			lookmore(){
				if(this.carlist.length<this.total){
					this.pageNum++
					this.search()
				}else{
					this.$u.toast('没有更多了')
				}
			},
			search(){
				this.$u.get('/prod-api/api/park/lot/record/list',{
					pageNum:this.pageNum,
					pageSize:5,
					entryTime:this.entertime,
					outTime:this.outtime
				}).then(res=>{
					this.showmore=true
					console.log(res);
					this.total=res.total
					res.rows.forEach(res=>{
						this.carlist.push(res)
					})
				})
			},
		}
	}
</script>

<style scoped>
	.carlist{
		display: flex;
		flex-direction: column;
		border-radius: 20rpx;
		border: 2rpx #999 solid;
		margin: 10rpx;
		padding: 10rpx;
	}
</style>
