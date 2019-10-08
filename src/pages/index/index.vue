<template>
	<div class="current-box">
		<section class="cur-header">
		  <div class="message"></div>
		  <div class="search">
			  <gc-input iconCode="#icon-color_target"></gc-input>
		  </div>
		  <div class="show-switch"></div>
		</section>
		<section class="cur-panel">
			<!--这里根据时间标签循环，待完善-->
			<gc-collapse tag="晚间"></gc-collapse>
		</section>
		<section class="cur-footer">

		</section>
	</div>
</template>

<script>
import card from '@/components/card'
import GcInput from '@/components/GcInput'
import GcCollapse from '@/components/GcCollapse'

export default {
    data () {
        return {
            motto: 'Hello miniprograme',
            userInfo: {
                nickName: 'mpvue',
                avatarUrl: '//mpvue.com/assets/logo.png'
            }
        }
    },

    components: {
        card,
        GcInput,
        GcCollapse
    },

    methods: {
        bindViewTap () {
            const url = '../logs/main'
            if (mpvuePlatform === 'wx') {
                mpvue.switchTab({ url })
            } else {
                mpvue.navigateTo({ url })
            }
        },
        clickHandle (ev) {
            console.log('clickHandle:', ev)
            // throw {message: 'custom test'}
        }
    },

    created () {
    // let app = getApp()
    }
}
</script>

<style lang="less" scoped>
.current-box {
	.cur-header {
		display: flex;
		flex-flow: row nowrap;
		padding: 0 25rpx;
		box-sizing: border-box;
		.message {
			position: relative;
			flex: 1;
			&::after {
				width: 65rpx;
				height: 65rpx;
				content: '';
				position: absolute;
				top: 50%;
				left: 0;
				transform: translateY(-50%);
				overflow: hidden;
				background-image: url('http://ww1.sinaimg.cn/large/00760Iw1gy1g7qn07eu5ij305k05kjrd.jpg');
				background-size: cover;
			}
		}
		.search {
			flex: 5;
		}
		.show-switch {
			position: relative;
			flex: 1;
			&::after {
				width: 65rpx;
				height: 65rpx;
				content: '';
				position: absolute;
				top: 50%;
				right: 0;
				transform: translateY(-50%);
				overflow: hidden;
				background-image: url('http://ww1.sinaimg.cn/large/00760Iw1gy1g7qn078ykxj305k05k74c.jpg');
				background-size: cover;
			}
		}
	}
	.cur-panel {
		padding: 0 25rpx;
		box-sizing: border-box;
	}
}
</style>
