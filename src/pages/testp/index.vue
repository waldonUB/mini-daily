<template>
	<div class="container">
		<div class="clickBox" @click="showLog">
			<button @click.stop="stopClickTest" class="catchBtn">测试阻止冒泡</button>
			<div @click.stop>
				<form report-submit="true" class="catchForm" @submit="showSubmitLog">
					<button form-type="submit" class="catchBtn">catchForm阻止冒泡</button>
				</form>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
	    name: 'testp',
		data () {
	        return {}
		},
		methods: {
            showLog () {
                console.log(`我是clickBox`)
			},
            stopClickTest () {
                console.log(`我是stopClickTest`)
			},
			showSubmitLog (e) {
                console.log(`showSubmitLog${e}`)
                console.log(`当前的formId为：${e.mp.detail.formId}`)
			}
		}
	}
</script>

<style scoped lang="less">
.container {
	.clickBox {
		width: 300px;
		height: 500px;
		border: 1px solid black;
		.catchBtn {
			width: 150px;
			height: 50px;
			color: black;
			font-size: 14px;
		}
		.catchForm {
			width: 150px;
			height: 100px;
			border: 1px solid black;
			.catchBtn {
				width: 100%;
				height: 50px;
				color: black;
				font-size: 14px;
			}
		}
	}
}
</style>
