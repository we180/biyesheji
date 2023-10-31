<template>
	<view>
		<view class="info">
			<!-- 详情页上方显示标题和发布时间，下方显示内容。 -->
			<h3 style="text-align: center;">{{newsinfo.title}}</h3>
			<h4 style="text-align: center;">{{newsinfo.publishDate}}</h4>
			<rich-text :nodes="newsinfo.content"></rich-text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				newsinfo:''
			}
		},
		methods: {
			async getData(){
				let res1=await this.$u.get('/prod-api/api/park/press/press/'+this.id)
				this.newsinfo=res1.data
				console.log(res1);
			}
		},
		onLoad(ops) {
			this.id=ops.id
			this.getData()
		}
	}
</script>

<style scoped>

</style>
