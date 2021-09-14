<template>
	<view style="height: 100%; width: 100%;">

		<uni-card is-full="true">
			<view>
				<view class="uni-textarea">
					<textarea placeholder="点击这里输入事件名称" />
				</view>
			</view>

		</uni-card>
		<view class="example-body">
			<uni-datetime-picker v-model="single" :border="true" type="date" />
		</view>
		<view class="isTopSw">
			<view class="isTop">
				<text>置顶</text>
			</view>
			<view>
				<switch checked="true" @change="" style="transform: scale(0.7);" color="pink" />
			</view>
		</view>
		<button type="primary" plain="true" :loading="false" style="width: 50%; margin-top: 40rpx;">保存</button>
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

<style scoped>
	.uni-textarea {
		padding: 10rpx;
	}

	.example-body {
		margin-top: 20rpx;
	}
	
	.isTopSw {
		padding: 20rpx;
		position: relative;
		margin-top: 20rpx;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}

	.isTopSw::before {
		position: absolute;
		z-index: 10;
		right: 0;
		top: 0;
		left: 0;
		height: 1px;
		content: "";
		transform: scaleY(.5);
		background-color: #c8c7cc;
	}

	.isTopSw::after {
		position: absolute;
		z-index: 10;
		right: 0;
		bottom: 0;
		left: 0;
		height: 1px;
		content: "";
		transform: scaleY(.5);
		background-color: #c8c7cc;
	}
</style>
