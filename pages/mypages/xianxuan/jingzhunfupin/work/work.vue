<template>
	<view>
		<view class="type">
			<u-icon name="error" label="收到的求助" label-pos="bottom" size="100" color="#2979ff" @click="toqiuzhu"></u-icon>
			<u-icon name="man-add" label="我帮扶的" label-pos="bottom" size="100" color="#2979ff" @click="tobangfu"></u-icon>
			<u-icon name="map" label="入户走访" label-pos="bottom" size="100" color="#2979ff" @click="tozoufang"></u-icon>
			<u-icon name="grid" label="我的案例" label-pos="bottom" size="100" color="#2979ff" @click="tomyanli"></u-icon>
		</view>
		<u-section title="所有扶贫案例" font-size="40"></u-section>
		<u-gap></u-gap>
		<view class="anlilist">
			<view class="anli">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_fupin/5.png" width="100%" height="200rpx" border-radius="20rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>走进精准扶贫“首倡地”——湖南湘西十八洞村</h3>
						<h4>扶贫主要参与人:塔塔露、塔塔露、桑克瑞德、于里昂热</h4>
						<text>2022/6/30</text>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="anli">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_fupin/6.png" width="100%" height="200rpx" border-radius="20rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>合作社撑起“茶叶楼”</h3>
						<h4>扶贫主要参与人:陈东、马超、刘洋</h4>
						<text>2022/7/10</text>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="anli">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_fupin/7.png" width="100%" height="200rpx" border-radius="20rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>龙头企业引领养鸡户致富</h3>
						<h4>扶贫主要参与人:王翠萍、陈亮吉、张伟光</h4>
						<text>2022/6/10</text>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="anli">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_fupin/8.png" width="100%" height="200rpx" border-radius="20rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>扶贫小额信贷</h3>
						<h4>扶贫主要参与人:丁真、蔡徐坤、艾伦</h4>
						<text>2022/2/10</text>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="anli">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_fupin/9.png" width="100%" height="200rpx" border-radius="20rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>电商扶贫</h3>
						<h4>扶贫主要参与人:王翠萍、陈亮吉、张伟光</h4>
						<text>2022/12/10</text>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="anli">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_fupin/10.png" width="100%" height="200rpx" border-radius="20rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>“金鸡帮扶”项目</h3>
						<h4>扶贫主要参与人:张鹏飞、王晓明、李雪、王勇、张芳</h4>
						<text>2022/1/10</text>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
			<view class="anli">
				<u-row>
					<u-col span="4">
						<u-image src="../../../../../static/myimgs/myimg_fupin/11.png" width="100%" height="200rpx" border-radius="20rpx"></u-image>
					</u-col>
					<u-col span="8">
						<h3>贫困村创业致富带头人培训</h3>
						<h4>扶贫主要参与人:郭亮、王丽、李宁、陈芳</h4>
						<text>2022/10/10</text>
					</u-col>
				</u-row>
			</view>
			<u-gap></u-gap>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {
			toqiuzhu(){
				uni.navigateTo({
					url:'qiuzhu/qiuzhu'
				})
			},
			tobangfu(){
				uni.navigateTo({
					url:'bangfu/bangfu'
				})
			},
			tozoufang(){
				uni.navigateTo({
					url:'zoufang/zoufang'
				})
			},
			tomyanli(){
				uni.navigateTo({
					url:'myanli/myanli'
				})
			},
		}
	}
</script>

<style scoped>
	.type {
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		flex-wrap: wrap;
	}

	.type>* {
		width: 25%;
		padding: 20rpx;
	}
</style>
