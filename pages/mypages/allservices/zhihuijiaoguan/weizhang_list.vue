<template>
	<view>
		<!-- 违法时间、违章地点、违章记分、罚款金额、处理状态 -->
		<!-- 默认显示5-6条记录，点击查看更多显示全部违章记录。 -->
		<view class="info" v-for="(item,weizhanglistid) in weizhanglist" :key="weizhanglistid" @click="toweizhang_De(weizhanglistid)">
			<h3>违法时间:{{item.badTime}}</h3>
			<h3>违章地点:{{item.illegalSites}}</h3>
			<h3>违章记分:{{item.deductMarks}}分</h3>
			<h3>罚款金额:{{item.money}}元</h3>
			<h3>处理状态:{{item.disposeState}}</h3>
		</view>
		<view class="lookmore">
			<u-button type="primary" @click="lookmore">查看更多</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				type:'',
				carnum:'',
				enginenum:'',
				total:0,
				pageNum:1,
				weizhanglist:[]
				
			}
		},
		methods: {
			toweizhang_De(id){
				uni.navigateTo({
					url:'weizhang_details?id='+this.weizhanglist[id].id
				})
			},
			lookmore(){
				if(this.weizhanglist.length<this.total){
					this.pageNum++
					this.getData()
				}else{
					this.$u.toast('没有更多了')
				}
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/traffic/illegal/list',{
					catType:this.type,
					licencePlate:this.carnum,
					engineNumber:this.enginenum,
					pageSize:5,
					pageNum:this.pageNum
				})
				this.total=res1.total
				res1.rows.forEach(res=>{
					this.weizhanglist.push(res)
				})
				console.log(res1);
			}
		},
		onLoad(ops) {
			this.type=ops.type
			this.carnum=ops.carnum
			this.enginenum=ops.enginenum
			this.getData()
		},
	}
</script>

<style scoped>
	.info{
		margin: 10rpx;
		padding: 10rpx;
		border: 2rpx solid #aaa;
		border-radius: 20rpx;
	}
</style>
