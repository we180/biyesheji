<template>
	<view>
		<!-- 选择需要回收垃圾种类，让工作人员了解需求。 -->
		<view class="input">
			<u-field label="垃圾种类" v-model="laji_type" @click="showtype=true" :disabled="true"></u-field>
			<u-action-sheet :list="type" @click="choosetype" v-model="showtype"></u-action-sheet>
			<u-field label="上门时间" v-model="time"></u-field>
			<u-field label="垃圾重量" ></u-field>
			<u-button type="success" @click="submit">提交</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				time:'',
				showtype:false,
				laji_type:'',
				type:[
					{
						text:'可回收垃圾'
					},
					{
						text:'其他垃圾'
					},
					{
						text:'厨余垃圾'
					},
					{
						text:'有害垃圾'
					}
				],
				
			}
		},
		methods: {
			choosetype(index){
				if(index==0){
					this.laji_type='可回收垃圾'
				}else if(index==1){
					this.laji_type='其他垃圾'
				}else if(index==2){
					this.laji_type='厨余垃圾'
				}else {
					this.laji_type='有害垃圾'
				}
			},
			submit(){
				this.$u.toast('提交成功')
				setTimeout(()=>{
					uni.navigateBack({
						delta:1
					})
				},700)
			}
		}
	}
</script>

<style scoped>

</style>
