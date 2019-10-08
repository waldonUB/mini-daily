<template>
  <div class="collapse">
	  <div class="toolbar">
		  <div class="tag">
			  <span>{{tag}}</span>
		  </div>
		  <div class="arrow" :class="direction"></div>
	  </div>
	  <div class="content"></div>
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
            toggle () {}
		}
    }
</script>

<style lang="less" scoped>
.collapse {
	.toolbar {

	}
}
</style>
