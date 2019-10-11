<template>
  <div class="collapse">
	  <div class="toolbar">
		  <div class="tag">
			  <span class="tag-font">{{tag}}</span>
		  </div>
		  <div @click="toggle" class="arrow" :class="direction"></div>
	  </div>
	  <div class="content">
		<!--限制个数为4个，自动换行，试试grid row？-->

	  </div>
  </div>
</template>

<script>
    export default {
        name: 'GcCollapse',
		props: {
            tag: {
                required: true,
                default: '任意时间'
			}
		},
        data () {
            return {
                direction: 'left'
            }
        },
		methods: {
            toggle () {
                this.direction = this.direction === 'left' ? 'down' : 'left'
			}
		}
    }
</script>

<style lang="less" scoped>
.collapse {
	box-sizing: border-box;
	padding: 30rpx 0;
	.toolbar {
		height: 50rpx;
		position: relative;
		display: flex;
		flex-flow: row nowrap;
		.tag {
			position: absolute;
			left: 0;
			top: 0;
			.tag-font {
				background-color: rgb(246, 247, 249);
				border-radius: 20rpx;
				padding: 5rpx 20rpx;
				font-size: 28rpx;
				font-weight: 800;
				color: #333333;
			}
		}
		.arrow {
			width: 50rpx;
			height: 100%;
			position: absolute;
			right: 0;
			top: 0;
			overflow: hidden;
			background-image: url('http://ww1.sinaimg.cn/large/00760Iw1gy1g7qn07971ej305k05kdfm.jpg');
			background-size: cover;
			&.left {
				transform: rotate(0deg);
				transition: all 0.1s ease-out;
			}
			&.down {
				transform: rotate(90deg);
				transition: all 0.1s ease-out;
			}
		}
	}
}
</style>
