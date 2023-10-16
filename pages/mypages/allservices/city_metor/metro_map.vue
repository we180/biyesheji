<template>
	<view>
		<view class="info">
			<u-row>
				<u-col span="4">
					<view class="linename" v-for="(item,all_linesid) in all_lines" :key="all_linesid">
						<h4>{{item.lineName}}</h4>
					</view>
				</u-col>
				<u-col span="8">
					<u-image width="100%" height="1000rpx" :src="baseUrl+map.imgUrl"></u-image>
				</u-col>
			</u-row>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				all_lines:[],
				map:''
			}
		},
		methods: {
			async getData(){
				let res1=await this.$u.get('/prod-api/api/metro/line/list')
				this.all_lines=res1.data
				console.log(res1);
				let res2=await this.$u.get('/prod-api/api/metro/city')
				this.map=res2.data
				console.log(res2);
			}
		},
		onLoad() {
			this.getData()
		}
	}
</script>

<style scoped>

</style>
