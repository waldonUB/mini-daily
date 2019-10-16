<template>
  <div class="setting-box">
	  <div class="setting-header">更多</div>
	  <div class="setting-content">
		  <div class="user-info">
			  <div :data-nickname="nickname"
				   class="head-img"
				   :style="{backgroundImage: 'url(' + headImg + ')'}"
				   @click="changeHeadImg">
			  </div>
		  </div>
		  <div class="func-cards">
			  <div class="card-box" v-for="item of funcList" :key="item.key">
				  <div :data-func="item.label" class="card-img" :style="{backgroundImage: 'url(' + item.value + ')'}"></div>
			  </div>
		  </div>
	  </div>
	  <div class="version"></div>
  </div>
</template>

<script>
    export default {
        name: 'Setting',
		data () {
            return {
                nickname: '未设置昵称',
				headImg: '//ww1.sinaimg.cn/large/00760Iw1gy1g7xjq1jci2j305k05kt8o.jpg',
                funcList: [
                    {
                        key: '1',
                        value: '//ww1.sinaimg.cn/large/00760Iw1gy1g7qn07crhjj305k05kmx6.jpg',
                        label: '准备礼物'
                    },
                    {
                        key: '2',
                        value: '//ww1.sinaimg.cn/large/00760Iw1gy1g7qn07c97sj305k05kglm.jpg',
                        label: '看书'
                    },
                    {
                        key: '3',
                        value: '//ww1.sinaimg.cn/large/00760Iw1gy1g7qn07i308j305k05kq30.jpg',
                        label: '听音乐'
                    },
                    {
                        key: '4',
                        value: '//ww1.sinaimg.cn/large/00760Iw1gy1g7qn07erhoj305k05kgln.jpg',
                        label: '拍照'
                    },
                    {
                        key: '5',
                        value: '//ww1.sinaimg.cn/large/00760Iw1gy1g7qn078ykxj305k05k74c.jpg',
                        label: '射击'
                    },
                    {
                        key: '6',
                        value: '//ww1.sinaimg.cn/large/00760Iw1gy1g7qn07crhjj305k05kmx6.jpg',
                        label: '准备礼物'
                    },
                    {
                        key: '7',
                        value: '//ww1.sinaimg.cn/large/00760Iw1gy1g7qn07c97sj305k05kglm.jpg',
                        label: '看书'
                    },
                    {
                        key: '8',
                        value: '//ww1.sinaimg.cn/large/00760Iw1gy1g7qn07i308j305k05kq30.jpg',
                        label: '听音乐'
                    },
                    {
                        key: '9',
                        value: '//ww1.sinaimg.cn/large/00760Iw1gy1g7qn07erhoj305k05kgln.jpg',
                        label: '拍照'
                    },
                    {
                        key: '10',
                        value: '//ww1.sinaimg.cn/large/00760Iw1gy1g7qn078ykxj305k05k74c.jpg',
                        label: '射击'
                    },
                    {
                        key: '11',
                        value: '//ww1.sinaimg.cn/large/00760Iw1gy1g7qn07crhjj305k05kmx6.jpg',
                        label: '准备礼物'
                    },
                    {
                        key: '12',
                        value: '//ww1.sinaimg.cn/large/00760Iw1gy1g7qn07c97sj305k05kglm.jpg',
                        label: '看书'
                    }
                ]
			}
		},
		methods: {
            /**
			 * 改变用户头像
			 * */
            changeHeadImg () {
                const vm = this
                wx.chooseImage({
                    sizeType: ['original', 'compressed'], // 可以指定是原图还是压缩图，默认二者都有
                    sourceType: ['album', 'camera'], // 可以指定来源是相册还是相机，默认二者都有
                    success: function (res) {
                        // 返回选定照片的本地文件路径列表，tempFilePath可以作为img标签的src属性显示图片
						console.log(`当前文件路径为：` + res.tempFiles[0].path)
						// 在手机上显示不出来？
                        vm.headImg = res.tempFiles[0].path
                    }
                })
			}
		},
		mounted () {
		}
    }
</script>

<style lang="less" scoped>
.setting-box {
	.setting-header {
		height: 60rpx;
		font-weight: 600;
		color: #333333;
		font-size: 28rpx;
		text-align: center;
	}
	.setting-content {
		.user-info {
			height: 160rpx;
			display: flex;
			justify-content: center;
			align-items: center;
			margin-bottom: 60rpx;
			.head-img {
				width: 140rpx;
				height: 140rpx;
				position: relative;
				background-position: center;
				background-size: cover;
				border: 1rpx solid #333333;
				border-radius: 50%;
				&::after {
					content: attr(data-nickname);
					width: 100%;
					text-align: center;
					position: absolute;
					bottom: -45rpx;
					font-weight: 600;
					font-size: 26rpx;
				}
			}
		}
		.func-cards {
			box-sizing: border-box;
			padding: 30rpx 100rpx;
			display: flex;
			flex-flow: row wrap;
			/*每行3个，在每行的中间加两边的margin就可以*/
			div:nth-child(3n + 2) {
				margin: 20rpx 5% 0;
			}
			.card-box {
				position: relative;
				width: 30%;
				height: 165rpx;
				box-sizing: border-box;
				background-color: rgb(255, 255, 255);
				border-radius: 8rpx;
				border: 1rpx solid rgb(243, 243, 241);
				margin-top: 20rpx;
				.card-img {
					position: absolute;
					top: 0;
					left: 20rpx;
					bottom: 60rpx;
					right: 20rpx;
					background-position: center;
					background-size: cover;
					&::after {
						content: attr(data-func);
						width: 100%;
						text-align: center;
						position: absolute;
						bottom: -30rpx;
						font-weight: 600;
						font-size: 26rpx;
					}
				}
			}
		}
	}
}
</style>
