<template>
	<view style="height: 100%; width: 100%;">
		<scroll-view scroll-y="true">
			<view class="annive-body">
				<view class="isTop">
					<uni-card isShadow="true">
						<view class="top-info">
							<view class="top-remind">
								<view class="title">
									<view class="font">
										<text>置顶的 ！</text>
									</view>
								</view>
								<view class="info">
									<view class="left-info">
										<text>出去吃火锅1</text>
									</view>
									<view class="info-type">
										<text>已经</text>
									</view>
								</view>
							</view>
							<view class="top-days-count">
								<view class="body">
									<text>100天</text>
								</view>
							</view>
						</view>
					</uni-card>
					<uni-card isShadow="true">
						<view class="top-info">
							<view class="top-remind">
								<view class="title">
									<view class="font">
										<text>置顶的 ！</text>
									</view>
								</view>
								<view class="info">
									<view class="left-info">
										<text>出去吃火锅1</text>
									</view>
									<view class="info-type">
										<text>已经</text>
									</view>
								</view>
							</view>
							<view class="top-days-count">
								<view class="body">
									<text>100天</text>
								</view>
							</view>
						</view>
					</uni-card>
				</view>
				<view class="other-date">
					<uni-card isShadow="true">
						<view class="other-date-body">
							<view class="left-info">
								距离上王者
							</view>
							<view class="info-type">
								已经
							</view>
							<view class="days-count">
								20年
							</view>
						</view>
					</uni-card>
					<uni-card isShadow="true">
						<view class="other-date-body">
							<view class="left-info">
								距离春节
							</view>
							<view class="info-type">
								还有
							</view>
							<view class="days-count">
								20年
							</view>
						</view>
					</uni-card>
					<uni-card isShadow="true">
						<view class="other-date-body">
							<view class="left-info">
								距离上爱上了卡上飞机喀什
							</view>
							<view class="info-type">
								还有
							</view>
							<view class="days-count">
								20年
							</view>
						</view>
					</uni-card>
					<uni-card isShadow="true">
						<view class="other-date-body">
							<view class="left-info">
								距离上王者
							</view>
							<view class="info-type">
								还有
							</view>
							<view class="days-count">
								20年
							</view>
						</view>
					</uni-card>
					<uni-card isShadow="true">
						<view class="other-date-body">
							<view class="left-info">
								距离上王者
							</view>
							<view class="info-type">
								还有
							</view>
							<view class="days-count">
								20年
							</view>
						</view>
					</uni-card>
					<uni-card isShadow="true">
						<view class="other-date-body">
							<view class="left-info">
								距离上王者
							</view>
							<view class="info-type">
								还有
							</view>
							<view class="days-count">
								20年
							</view>
						</view>
					</uni-card>
					<uni-card isShadow="true">
						<view class="other-date-body">
							<view class="left-info">
								距离上王者
							</view>
							<view class="info-type">
								还有
							</view>
							<view class="days-count">
								20年
							</view>
						</view>
					</uni-card>
					<uni-card isShadow="true">
						<view class="other-date-body">
							<view class="left-info">
								距离上王者
							</view>
							<view class="info-type">
								还有
							</view>
							<view class="days-count">
								20年
							</view>
						</view>
					</uni-card>
					<uni-card isShadow="true">
						<view class="other-date-body">
							<view class="left-info">
								距离上王者
							</view>
							<view class="info-type">
								还有
							</view>
							<view class="days-count">
								20年
							</view>
						</view>
					</uni-card>
				</view>
			</view>
		</scroll-view>
		<view>
			<uni-fab :pattern="fabSetting.pattern" :horizontal="fabSetting.horizontal" :vertical="fabSetting.vertical"
				:direction="fabSetting.direction" @fabClick="fabClick" :popMenu="false"></uni-fab>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				fabSetting: {
					range: ['2021-03-8', '2021-4-20'],
					pattern: {
						buttonColor: "pink"
					},
					horizontal: "right",
					vertical: "bottom",
					direction: "vertical",
				},
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
	.annive-body {}

	.isTop {}

	.uni-card {
		height: 100% !important;
	}
	
	.top-info {
		height: 150px;
		display: flex;
	}

	.top-remind {
		display: flex;
		flex-direction: column;
		flex: 1;
	}

	.top-remind .title {
		display: flex;
		justify-content: center;
		align-items: center;
		flex: 1;
		padding-bottom: 20rpx;
		border-bottom: 1px solid #c8c7cc;
	}

	.top-remind .title .font {
		padding: 5%;
		border-radius: 10%;
		font-size: 50rpx;
	}

	.top-remind .info {
		display: flex;
		justify-content: center;
		align-items: center;
		font-size: 40rpx;
		font-weight: 600;
		flex: 1;
	}

	.top-remind .info .left-info {
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: nowrap;
		flex: 6;
	}

	.top-remind .info .info-type {
		flex: 2;
	}

	.top-days-count {
		display: flex;
		justify-content: center;
		align-items: center;
		flex: 1;
	}

	.top-days-count .body {
		border-radius: 5%;
		color: #FFFFFF;
		text-align: center;
		padding: 10rpx;
		background-color: #f29696;
		font-size: 80rpx;
		font-weight: 600;
	}

	.other-date .other-date-body {
		display: flex;
		justify-content: center;
		align-items: center;
		font-size: 40rpx;
		padding: 10rpx;
	}

	.other-date .other-date-body .left-info {
		flex: 6;
	}

	.other-date .other-date-body .info-type {
		flex: 2;
	}

	.other-date .other-date-body .days-count {
		color: #f29696;
		flex: 2;
	}
</style>
