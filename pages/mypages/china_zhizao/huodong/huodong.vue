<template>
	<view>
		<u-tabs :list="list" @change="changetab" :current="current" style="text-align: center;"></u-tabs>
		<view class="newzhanhui" v-for="(item,index) in 6" :key="index" v-if="show==0" @click="tohuodong_De(show)">
			<u-row>
				<u-col span="4">
					<u-image width="100%" height="220rpx" src="../../../../static/myimgs/china_zhizao/file_20220502cs42.jpg"></u-image> 
				</u-col>
				<u-col span="8">
					<h3>第十八届中国国际轮胎博览会</h3>
					<text class="u-line-4">中国国际轮胎博览会是由海富展览服务有限公司于 2003 年初成立创办, 为行业提供一个国际性的贸易和洽谈平台。展品范围包括各种规格的轮胎、轮圈、轮胎保修设备、翻胎原料及设备、轮胎生产原料及设备、轮胎配件等相关产品与技术。</text>
				</u-col>
			</u-row>
		</view>
		<view class="newzhanhui" v-for="(item,index2) in 6" :key="index2+9" v-if="show==1" @click="tohuodong_De(show)">
			<u-row>
				<u-col span="4">
					<u-image width="100%" height="220rpx" src="../../../../static/myimgs/china_zhizao/file_20220502cs49.jpg"></u-image> 
				</u-col>
				<u-col span="8">
					<h3>第七届深圳国际电子与工业智造展、第五届国际半导体展</h3>
					<text class="u-line-4">电子元器件展区无源器件、半导体分立器件/ IGBT5G核心元器件特种电子、元器件、电源管理、传感器、储存器、连接器继电器、线缆、接插器件 晶振、电阻、电位器磁性元件、滤波元件 PCB板、电机风扇电声器件、显示器件、二极管、三极管滤波元件、开关及元器件材料及设备等。IC设计、芯片展区IC及相关电子产品设计</text>
				</u-col>
			</u-row>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				show:0,
				current:0,
				list:[
					{
						name:'最新展会'
					},
					{
						name:'过往展会'
					}
				],
				
			}
		},
		methods: {
			changetab(index){
				this.current=index
				this.show=index
			},
			tohuodong_De(show){
				uni.navigateTo({
					url:'huodong_details?show='+show
				})
			},
		}
	}
</script>

<style scoped>
	.newzhanhui{
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 20rpx;
		border: 2rpx solid #aaa;
	}
</style>
