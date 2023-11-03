<template>
	<view>
		<view class="dongtai1">
			<view class="index" @click="tohuodong_De">
				<u-row>
					<u-col span="4">
						<image src="../../../../../static/myimgs/myimg_dangjian/u=237204657,1833581701&fm=26&fmt=auto&gp=0.jpg" mode="" style="width: 230rpx; height: 230rpx;"></image>
					</u-col>
					<u-col span="8">
						<h3>智慧党建活动室建设解决方案</h3>
						<text class="u-line-3">“智慧党建”是“互联网 ＋ 党建”的高级阶段，侧重用大数据分析产生新认识，预测新动向、提供新思路。
“智慧党建”是运用信息化新技术，整合各方资源，更有效地加强组织管理，提高服务群众水平</text>
					</u-col>
				</u-row>
				<u-gap></u-gap>
				<u-row>
					<u-col span="4">
						<image src="../../../../../static/myimgs/myimg_dangjian/u=604788707,102911010&fm=26&fmt=auto&gp=0.jpg" mode="" style="width: 230rpx; height: 230rpx;"></image>
					</u-col>
					<u-col span="8">
						<h3>技术赋能“党建文化+直播”智慧党建新模式</h3>
						<text class="u-line-3">印象中的党建活动常以线下座谈会或参观红色教育基地的形式进行，一次党建活动需要前期进行人员组织和活动方案规划，但线下的活动仅限于党员的时间安排和到场人员数量，</text>
					</u-col>
				</u-row>
			</view>
		</view>
		<u-gap></u-gap>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			tohuodong_De(){
				uni.navigateTo({
					url:'hudong_de'
				})
			}
		}
	}
</script>

<style scoped>

</style>
