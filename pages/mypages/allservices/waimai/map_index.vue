<template>
	<u-index-list :scrollTop="scrollTop" :index-list="indexList">
		<view v-for="(item, index) in list" :key="index">
			<u-index-anchor :index="item.letter" />
			<view class="list-cell u-border-bottom" v-for="(item1, index1) in item.data" :key="index1" @click="back(index,index1)">
				{{item1.name}}
			</view>
		</view>
	</u-index-list>
</template>

<script>
	import indexList from "@/common/index.list.js";
	const letterArr = indexList.list.map(val => {
		return val.letter;
	})
	export default {
		data() {
			return {
				scrollTop: 0,
				indexList: letterArr,
				list: indexList.list
			}
		},
		methods: {
			back(index,index1) {
				// console.log(this.list[index].data[index1].name);
				uni.setStorageSync('address',this.list[index].data[index1].name)
				uni.switchTab({
					url:'waimai',
				})
			}
		},
		onPageScroll(e) {
			this.scrollTop = e.scrollTop;
		}
	}
</script>

<style lang="scss" scoped>
	.list-cell {
		display: flex;
		box-sizing: border-box;
		width: 100%;
		padding: 10px 24rpx;
		overflow: hidden;
		color: $u-content-color;
		font-size: 14px;
		line-height: 24px;
		background-color: #fff;
	}
</style>
