<template>
	<view>
		<u-tabs :list="list" style="text-align: center;" :current="current" @change="changetab"></u-tabs>
		<view class="wancheng">
			
		</view>
		<view class="baoming">
			
		</view>
		<view class="quxiao">
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[
					{
						name:'已完成'
					},
					{
						name:'已报名'
					},
					{
						name:'已取消'
					}
				],
				current:0,
				huodong_wancheng:[],
				huodong_baoming:[],
				huodong_quxiao:[]
				
				
			}
		},
		methods: {
			changetab(index){
				this.current=index
			},
			async getData(){
				let res1=await this.$u.get('/prod-api/api/volunteer-service/activity/my-list/1')
				this.huodong_wancheng=res1.rows
				console.log(res1);
				let res2=await this.$u.get('/prod-api/api/volunteer-service/activity/my-list/2')
				this.huodong_wancheng=res2.rows
				console.log(res2);
				let res3=await this.$u.get('/prod-api/api/volunteer-service/activity/my-list/3')
				this.huodong_wancheng=res3.rows
				console.log(res3);
			},
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>

</style>
