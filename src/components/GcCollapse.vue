<template>
  <div class="collapse">
	  <div class="toolbar">
		  <div class="tag">
			  <span class="tag-font">{{tag}}</span>
		  </div>
		  <div @click="toggle" class="arrow" :class="direction"></div>
	  </div>
	  <ul class="content">
		<!--限制个数为4个，自动换行，试试grid row？-->
        <li :key="item.key" v-for="item of todoList">
			<div :data-text="item.label" class="circle-img" :style="{backgroundImage: 'url(' + item.value + ')'}">
			</div>
		</li>
	  </ul>
  </div>
</template>

<script>
    export default {
        name: 'GcCollapse',
		props: {
            tag: {
                required: true,
                default: '任意时间'
			},
            todoList: {
                required: true,
				default: () => []
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
	.content {
		list-style: none;
		display: flex;
		flex-flow: row wrap;
		box-sizing: border-box;
		padding: 20rpx 0 50rpx;
		li {
			position: relative;
			padding: 0 0 25% 25%;
			.circle-img {
				box-sizing: border-box;
				position: absolute;
				left: 30rpx;
				top: 30rpx;
				right: 30rpx;
				bottom: 30rpx;
				border-radius: 50%;
				border: 1px solid #333333;
				background-size: cover;
				background-position: center;
				&::after {
					width: 100%;
					content: attr(data-text);
					position: absolute;
					bottom: -40rpx;
					text-align: center;
					font-size: 26rpx;
					color: rgb(65, 62, 63);
					font-weight: 600;
				}
			}
		}
	}
}
</style>
