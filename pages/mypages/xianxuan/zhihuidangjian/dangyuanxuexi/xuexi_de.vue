<template>
	<view>
		<view class="">
			<h2 style="text-align: center;">山东城市建设职业学院智慧党建应用</h2>
			<u-gap></u-gap>
			<view style="text-align: center;">
				<audio src="../../../../../static/myimgs/myimg_dangjian/1759.mp3" name="一步一个脚印" author="大司马" :controls="true"
					poster="../../../../../static/myimgs/myimg_dangjian/u=1283301471,2626968760&fm=26&fmt=auto&gp=0.jpg"></audio>
			</view>
			<u-gap></u-gap>
			<view class="video" style="text-align: center;">
				<video src="../../../../../static/myimgs/myimg_dangjian/video01.mp4" style="width: 100%;"></video>
			</view>
			<u-gap></u-gap>
			<h4>微加智慧党建的微党课，根据组织需求上传符合学校的学习资料、文件，不仅可以上传图文资料还能上传视频资料。
				使用前:组织内的学习培训任务很难有量化的检测，谁学谁没学，学了多少都比较模糊。
				使用后:平台自动记录每名党员的学习时长，学习课程明细，并且以积分的形式激励党员积极参加组织内的学习培训，极大地激发了党员的自主学习意识，并且学习完后平台提供在线考试进行学习效果评测，从学习，到强化，做到内化于心，外化于行。
			</h4>
			<view class="input" >
				<u-input placeholder="请输入评论" border="border" @click="toxuexi_comment"></u-input>
			</view>

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
			toxuexi_comment(){
				uni.navigateTo({
					url:'xuexi_comment'
				})
			},
		}
	}
</script>

<style scoped>
	.input{
		position: fixed;
		bottom: 0;
		width: 100%;
	}
</style>
