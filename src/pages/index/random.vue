<template>
    <div @touchmove.prevent>
        <div id="random"></div>
    </div>
</template>

<script>
	import Ball from "../../assets/js/ball";

	export default {
		name: "random",
        data(){
			return {}
        },
		mounted() {
			var backgroundLayer;
			var w = document.body.clientWidth;
			var h = document.body.clientHeight;
			var angleX = 0;
			var angleY = 0;
			var centerX = w/2;
			var centerY = h/2;
			var range = 50;
			var xSpeed = 0.07;
			var ySpeed = 0.11;
			var ball;

			var stage = new annie.Stage('random',w,h,60,annie.StageScaleMode.SHOW_ALL,0);
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
	            ball.x = centerX + Math.sin(angleX)*range;
	            ball.y = centerY + Math.sin(angleY)*range;
	            angleX+=xSpeed;
	            angleY+=ySpeed;
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
