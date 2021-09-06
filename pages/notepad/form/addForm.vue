<template>
	<view style="height: 100%; width: 100%;">
		<view class="example-body">
			<uni-datetime-picker v-model="single" :border="false" type="date"/>
		</view>
		<uni-card is-full="true">
			<view>
				<view class="uni-textarea">
					<textarea  placeholder="请输入..." />
				</view>
			</view>
		</uni-card>
		 <button type="primary" plain="true" loading="true" style="margin-top: 80rpx;">保存</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				single: '2021-04-3',
				pattern: {
					buttonColor: "pink"
				},
				horizontal: "right",
				vertical: "bottom",
				direction: "vertical",

			}
		},
		methods: {
			fabClick() {
				uni.navigateTo({
					url: "form/addForm"
				})
			}
		}
	}
</script>

<style>
</style>
