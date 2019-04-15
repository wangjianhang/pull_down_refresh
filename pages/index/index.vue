<template>
	<view>
		<cu-custom bgColor="bg-gradual-blue" :isBack="true">
			<block slot="backText">返回</block>
			<block slot="content">主页</block>
			<block slot="right">
				<view class="action">
					<text @click="showOption" class="action">筛选</text>
				</view>
				
			</block>
		</cu-custom>
		
		<pull-down-refresh  ref="pullDown" @on-pull-down="onPullDown">
			<view class="cu-bar bg-white align-center flex-direction " style="height: 500upx;" >
				<text class="action">{{content}}</text>
			</view>
		</pull-down-refresh>
		
		
		<view class="cu-modal" :class="isShow?'show':''" @tap="hideModal" >
			<view class="cu-dialog" @tap.stop>
				
				<view class="cu-form-group">
					<view class="title">地区</view>
					<input placeholder="两字短标题" name="input"></input>
				</view>
				<view class="cu-form-group">
					<view class="title">输入框</view>
					<input placeholder="三字标题" name="input"></input>
				</view>
				<view class="cu-form-group">
					<view class="title">收货地址</view>
					<input placeholder="统一标题的宽度" name="input"></input>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import PullDownFresh from '@/components/pullDownRefresh.vue'
	export default {
		data() {
			return {
				isShow : false,
				content:'内容'
			}
		},
		components:{
			'pull-down-refresh':PullDownFresh
		},
		onLoad(option) {
			
		},
		
		methods: {
			onPullDown() {
				//模拟ajax请求
				setTimeout(()=>{
					this.content = "新内容"
					this.$refs.pullDown.onPullDownFinish() //调用子组件完成方法
				},1000)
			},
			showOption(e){
				this.isShow = true
			},
			hideModal(){
				this.isShow = false
			},
			toAbout(){
				uni.navigateTo({
					url:'about'
				})
			}
		}
	}
</script>

<style>
	
</style>
