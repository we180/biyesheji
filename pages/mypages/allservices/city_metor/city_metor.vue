<template>
	<view>
		<view class="head">
			<u-navbar back-text="返回" title="城市地铁">
				<u-icon name="map" color="#2979ff" size="50" label="地铁地图" slot="right" style="margin-right: 20rpx;" @click="tomap"></u-icon> 
			</u-navbar> 
		</view>
		<view class="info">
			<!-- 地铁路线名称、下一站名称、到达本站时长 -->
			<view class="line" v-for="(item,line_indexid) in line_index" :key="line_indexid" @click="tometor_De(line_indexid)">
				<h2>{{item.lineName}}</h2>
				<h3>下一站:{{item.nextStep.name}}</h3>
				<h3>到达本站时长:{{item.reachTime}}分钟</h3>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				linelist:[],
				line_index:[]
			}
		},
		methods: {
			tomap(){
				uni.navigateTo({
					url:'metro_map'
				})
			},
			tometor_De(id){
				uni.navigateTo({
					url:'metor_details?title='+this.line_index[id].lineName+'&id='+this.line_index[id].lineId
				})
			},
			async getData(){
				// let res1=await this.$u.get('/prod-api/api/metro/step/list?name=建国门')
				// this.linelist=res1.rows
				// console.log(res1);
				let res2=await this.$u.get('/prod-api/api/metro/list?currentName=建国门')
				this.line_index=res2.data
				console.log(res2);
			},
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>
	.line{
		border-bottom: #aaa 2px dashed;
		margin: 10rpx;
		padding: 10rpx;
	}
</style>
