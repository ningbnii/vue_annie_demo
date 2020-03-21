<template>
    <div @touchmove.prevent>
        <div id="pulse"></div>
    </div>
</template>

<script>
	import Ball from "../../assets/js/ball";

	export default {
		name: "pulse",
        data(){
			return {}
        },
		mounted() {
			var backgroundLayer;
			var w = document.body.clientWidth;
			var h = document.body.clientHeight;
			var angle = 0;
			var centerScale = 1;
			var range = 1;
			var speed = 0.05;
			var ball;

			var stage = new annie.Stage('pulse',w,h,60,annie.StageScaleMode.SHOW_ALL,0);
			main();

            function main() {
            	initBackgroundLayer();
	            ball = new annie.Shape();
	            ball.x = w/2;
	            ball.y = h/2;
	            backgroundLayer.addChild(ball);
	            ball.beginFill('#ff0000');
	            ball.drawCircle(0,0,20);
	            ball.endFill();
	            backgroundLayer.addEventListener(annie.Event.ENTER_FRAME,onframe);
            }

            function onframe() {
	            ball.scaleX = ball.scaleY = centerScale + Math.sin(angle)*range;
	            angle+=speed;
            }

			function initBackgroundLayer() {
				let s = this;
				backgroundLayer = new annie.Sprite();
				stage.addChild(backgroundLayer);
			}
		},
        destroy(){}
	};
</script>

<style scoped>
</style>
