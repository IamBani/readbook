<template>
	<view class="content">
		<u-section font-size="32" :show-line="false" title="排行榜" sub-title="查看更多"></u-section>
		<view class="title">
			<u-tag class="tag" type="info" :border-color="index === i?'#f4ea2a':''" :text="item.title" shape="circle" :color="index===i?'#fff':'#909399'"
			 :bg-color="index===i?'#f4ea2a':'#fff'" v-for="(item,i) in list" :key="i" @click="tag(i)" />
		</view>
		<view class="rankings u-flex u-flex-wrap">
			<view class="u-flex box" v-for="(item,index) in ranLinst" :key="item.rank">
				<view class="u-relative">
					<image mode="aspectFit" style="width: 160rpx; height: 200rpx;" :src="item.image"></image>
					<u-badge :offset=[3,8] type="error" count="免费"></u-badge>
				</view>
				<view class="u-flex-1 u-flex-col titleRight">
					<text class="u-flex-2">{{item.title}}</text>
					<text class="u-flex-1 s_text">{{item.number}}万人在读</text>
					<view class="u-flex-1" v-if="ranking(item.rank)">
						<text class="top">Top</text>
						<text class="rank">{{item.rank}}</text>
					</view>
					<view class="u-flex-1" v-else>
						<text class="telrank">{{item.rank}}</text>
					</view>
				</view>
			</view>
		</view>
		<u-section class="u-m-t-25 u-m-b-20" font-size="32" :show-line="false" title="书友推荐">
			<view slot="right">
				换一换 <u-icon name="reload" class="u-m-l-8"></u-icon>
			</view>
		</u-section>
		<view class="u-flex u-col-top u-row-between">
			<view class="u-flex-1" v-for="(item,index) in rowLinst" :key="index">
				<view class="u-relative">
					<image mode="aspectFit" style="width: 160rpx; height: 200rpx;" :src="item.image"></image>
					<u-badge :offset=[3,24] type="error" count="免费"></u-badge>
				</view>
				<view class="">
					{{item.title}}
				</view>
			</view>
		</view>

		<u-section class="u-m-t-25 u-m-b-20" font-size="32" :show-line="false" title="精品完本" sub-title="查看更多">
		</u-section>
		<view class="u-flex u-col-top u-row-between">
			<view class="u-flex-1" v-for="(item,index) in rowLinst" :key="index">
				<view class="u-relative">
					<image mode="aspectFit" style="width: 160rpx; height: 200rpx;" :src="item.image"></image>
					<u-badge :offset=[3,24] type="error" count="免费"></u-badge>
				</view>
				<view class="">
					{{item.title}}
				</view>
			</view>
		</view>

		<u-section class="u-m-t-25 u-m-b-20" font-size="32" :show-line="false" title="猜你喜欢" :right="false">
		</u-section>
		<view class="like">
			<view v-for="(item,index) in dataList" :key="index" class="u-flex boxlike">
				<view class="u-relative">
					<image mode="aspectFit" style="width: 160rpx; height: 200rpx;" :src="item.image"></image>
					<u-badge :offset=[3,8] type="error" count="免费"></u-badge>
				</view>
				<view class="u-flex-col u-p-10 leftdes">
					<text class="bookname">{{item.booksname}}</text>
					<text class="u-line-2 u-m-t-15">{{item.describe}}</text>
					<text class="u-m-t-10">{{item.author}}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				index: 0,
				list: [{
					title: '男生人气',
				}, {
					title: '女生人气',
				}, {
					title: '男生飙升',
				}, {
					title: '女生飙升'
				}],
				rowLinst: [{
					image: require("../../assets/image/1.jpeg"),
					title: '美女总裁的上门女婿',
				}, {
					image: require("../../assets/image/2.jpeg"),
					title: '完美世界',
				}, {
					image: require("../../assets/image/3.jpeg"),
					title: '庆余年',
				}, {
					image: require("../../assets/image/4.jpeg"),
					title: '都市最强特种兵',
				}],
				ranLinst: [{
					image: require("../../assets/image/1.jpeg"),
					title: '美女总裁的上门女婿',
					number: '11.1',
					rank: 1,
				}, {
					image: require("../../assets/image/2.jpeg"),
					title: '完美世界',
					number: '13.2',
					rank: 2
				}, {

					image: require("../../assets/image/3.jpeg"),
					title: '庆余年',
					number: '13.2',
					rank: 3
				}, {
					image: require("../../assets/image/4.jpeg"),
					title: '都市最强特种兵',
					number: '13.2',
					rank: 4
				}, {
					image: require("../../assets/image/5.jpeg"),
					title: '都市最强修真妖孽',
					number: '13.2',
					rank: 5
				}, {
					image: require("../../assets/image/6.jpeg"),
					title: '我的绝美女神老师',
					number: '13.2',
					rank: 6
				}],
				dataList: [{
					image: require('../../assets/image/2.jpeg'),
					booksname: '不知道啥吞了',
					describe: '此书又名《不知道啥吞了我的功德怎么办》《论寻回功德的一二法》…… 白桑在飞升之时，突然被不知名物体劈头打到了陌生空间',
					author: "未来"
				}, {
					image:require('../../assets/image/3.jpeg'),
					booksname:'精品小立场',
					describe:'到修仙文中一集死的炮灰，夏初昭果断开始自救模式。 结果救者救着，却发现—— 她随手写的手札，成了众多强者争夺的“天书”。 她因偷懒炼制的丹炉，成了炼丹师们争夺的“神器”。',
					author:'障碍小组'
				},{
					image:require("../../assets/image/4.jpeg"),
					booksname:'精品教师',
					describe:'路星心喝个奶茶的功夫就穿越到了追读的小说《古代继承者们》中。 本以为穿成了身无分文，流浪街头的路人，结果在',
					author:'吃软怒'
				}],
			}
		},
		onLoad() {

		},
		onNavigationBarSearchInputClicked() {
			uni.navigateTo({
				url: '../search/search'
			})
		},
		methods: {
			tag(index) {
				console.log(index)
				this.index = index
			},
			ranking(index) {
				if (index === 1 || index === 2 || index === 3) {
					return true
				}
				return false
			}
		}
	}
</script>

<style lang="scss" scoped>
	.content {
		padding: 20rpx 20rpx 0;

		.title {
			.tag {
				margin: 15rpx 0;

				&:not(:first-child) {
					margin-left: 20rpx;
				}
			}
		}

		.rankings {
			.box {
				align-items: stretch;
				width: 50%;
				padding: 8rpx 8rpx 8rpx 0;

				.titleRight {
					// padding: 10rpx;
					margin-left: 5rpx;

					.s_text {
						color: $u-tips-color;
					}

					.rank {
						margin-left: 8rpx;
						font-size: 40rpx;
						color: $u-type-error;
					}

					.top {
						color: $u-type-error;
					}

					.telrank {
						font-size: 40rpx;
						color: $u-light-color;
					}
				}
			}
		}
		.like{
			.boxlike,.leftdes{
				align-items:stretch;
				.bookname{
					font-size: $uni-font-size-lg;
					color: $u-main-color;
					font-weight: 700;
				}
			}
		}
	}
</style>
