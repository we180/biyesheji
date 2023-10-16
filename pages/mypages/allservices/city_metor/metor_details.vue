<template>
	<view>
		<view class="head">
			<u-navbar back-text="返回" :title="title"></u-navbar> 
		</view>
		<view class="lineinfo">
			<!-- 剩余时间、间隔几站、剩余距离 -->
			<h2>始发站:{{lineinfo.first}}</h2>
			<h2>终点站:{{lineinfo.end}}</h2>
			<h3>剩余时间:{{lineinfo.remainingTime}}分钟</h3>
			<h3>间隔:{{lineinfo.stationsNumber}}站</h3>
			<h3>剩余距离:{{lineinfo.km}}km</h3>
			<h4>首班时间:{{lineinfo.startTime}}</h4>
			<h4>末班时间:{{lineinfo.endTime}}</h4>
		</view>
		<u-gap></u-gap>
		<view class="lines">
			<scroll-view scroll-x="true" >
				<view class="all_lines">
					<view class="stop" v-for="(item,linelistid) in lineinfo.metroStepList" :key="linelistid">
						<u-icon name="map" color="#2979ff" size="46" v-if="item.name==lineinfo.runStationsName"></u-icon> 
						<text style="font-size: 40rpx;font-weight: 550;">{{item.name}}</text>
					</view>
				</view>
			</scroll-view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title:'',
				id:'',
				lineinfo:''
			}
		},
		methods: {
			async getData(){
				let res1=await this.$u.get('/prod-api/api/metro/line/'+this.id)
				this.lineinfo=res1.data
				console.log(res1);
			}
		},
		onLoad(ops) {
			this.title=ops.title
			this.id=ops.id
			this.getData()
		}
	}
</script>

<style scoped>
	.lineinfo{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
	h3{
		color: red;
	}
	.lineinfo>*{
		padding: 6rpx;
	}
	.all_lines{
		display: flex;
		flex-direction: row;
	}
	.lines{
		background-color: #ccc;
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		
	}
	.stop{
		margin: 10rpx;
	}
</style>
