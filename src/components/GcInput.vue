<template>
	<div class="input-box">
	 	<input type="text" class="icon-input" placeholder="输入习惯名称">
		<div class="icon" :class="locate"></div>
    </div>
</template>

<script>
export default {
    name: 'GcInput',
    props: {
        iconCode: {
            default: ''
        },
        locate: {
            default: 'prefix'
        }
    },
    computed: {
    }

}
</script>

<style lang="less" scoped>
.input-box {
    position: relative;
	box-sizing: border-box;
    .icon-input {
        height: 65rpx;
        outline: none;
        border-radius: 8rpx;
		box-sizing: border-box;
		padding: 0 55rpx;
		border: 1rpx solid rgb(237, 241, 242);

    }
	.icon {
		width: 1em;
		height: 1em;
		overflow: hidden;
		background-image: url('http://ww1.sinaimg.cn/large/00760Iw1gy1g7qn07vxppj305l05ka9x.jpg');
		background-size: cover;
	}
    .prefix {
        position: absolute;
        left: 15rpx;
        top: 50%;
        transform: translateY(-50%);
        z-index: 9;
    }
    .suffix {
        position: absolute;
        right: 10rpx;
        top: 50%;
        transform: translateY(-50%);
		z-index: 9;
    }
}

</style>
