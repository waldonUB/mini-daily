<template>
	<div class="input-box">
        <!-- <input type="text" class="icon-input"> -->
        <svg class="icon" aria-hidden="true" :class="locate">
            <use xlink:href="#icon-icon-11"></use>
        </svg>
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
    .icon-input {
        width: 100%;
        height: 65rpx;
        background-color: rgb(237, 241, 242);
        outline: none;
        border-radius: 8rpx;
    }
    .prefix {
        position: absolute;
        left: 8rpx;
        top: 50%;
        transform: translateY(-50%);
        z-index: 9;
    }
    .suffix {
        position: absolute;
        right: 8rpx;
        top: 50%;
        transform: translateY(-50%);
    }

}

</style>