<template>
	<view style="height: 100%; width: 100%;">

		<view class="" style="height: 100%;">
			<uni-card isShadow="true" style="height: 100%;">

				<view class="example-body">
					<uni-datetime-picker v-model="single" :border="false" type="date" />
				</view>
				<view>
					<uni-data-checkbox v-model="value" :localdata="range" @change="change" mode="button"
						selectedColor="pink"></uni-data-checkbox>
				</view>
				<view class="acount-body">
					<view class="account-label">
						<text>￥</text>
					</view>
					<view class="account-number">
						<input class="account-input" type="digit" confirm-type="done" :value="123123" />
					</view>
				</view>

			</uni-card>
		</view>
		<uni-card isShadow="true" style="height: 100%;">
			<view class="remark">
				<view class="remark-label">
					<text>备注信息</text>
				</view>
				<view class="remark-body">
					<textarea value="" placeholder="请在此填写 . ." :maxlength="100" :auto-height="true"
						style="min-height: 200rpx; " />
				</view>
			</view>
		</uni-card>
		<button type="primary" plain="true" :loading="false" style="margin-top: 50rpx; width: 50%; ">保存</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				range: [{
					"value": 0,
					"text": "支出"
				}, {
					"value": 1,
					"text": "收入"
				}],
				single: '2021-04-3',
				record: {
					amount: '',
					remark: ''
				}

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
	.acount-body {
		display: flex;
		margin-top: 40rpx;
		margin-bottom: 50rpx;
		font-size: 50rpx;
	}

	.account-label {
		font-weight: 500;
		flex: 0;
		padding-right: 5rpx;
	}

	.account-number {
		position: relative;
		padding: 5rpx;
	}

	.account-input {}

	.account-number::before {
		position: absolute;
		z-index: 10;
		right: 0;
		bottom: 0;
		left: 0;
		height: 1px;
		content: "";
		background-color: #c8c7cc;
	}

	.account-input {
		height: 100%;
	}

	.remark {
		position: relative;
	}

	.remark .remark-body {
		margin-top: 30rpx;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.remark .remark-label .text {
		position: absolute;
		top: 0;
	}
</style>
