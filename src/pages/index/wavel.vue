<template>
    <div>
        <div id="wavel"></div>
    </div>
</template>

<script>
	import Ball from "../../assets/js/ball";

	export default {
		name: "wavel",
		mounted() {
			var backgroundLayer;
			var w = document.body.clientWidth;
			var h = document.body.clientHeight;
			var angle = 0;
			var centerY = h/2;
			var range = 50;
			var xspeed = 1;
			var yspeed = 0.05;
			var ball;

			var stage = new annie.Stage('wavel',w,h,60,annie.StageScaleMode.SHOW_ALL,0);
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
				ball.x += xspeed;
				ball.y = centerY + Math.sin(angle) * range;
				angle+= yspeed;
			}

			function initBackgroundLayer() {
				let s = this;
				backgroundLayer = new annie.Sprite();
				stage.addChild(backgroundLayer);
			}
		},
		methods: {

		}
	};
</script>

<style scoped>
</style>
