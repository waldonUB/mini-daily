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
		  <div class="func-cards"></div>
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
				headImg: '//ww1.sinaimg.cn/large/00760Iw1gy1g7xjq1jci2j305k05kt8o.jpg'
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
                        // vm.headImg = res.tempFiles[0].path
						debugger
                        vm.setData({
                            headImg: res.tempFiles[0].path
                        })
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
	}
}
</style>
