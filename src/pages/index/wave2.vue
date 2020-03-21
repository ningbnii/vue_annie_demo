<template>
    <div @touchmove.prevent>
        <div id="wave2"></div>
    </div>
</template>

<script>
	export default {
		name: "wave2",
        data(){
			return {}
        },
		mounted() {
			var backgroundLayer;
			var w = document.body.clientWidth;
			var h = document.body.clientHeight;
			var angle = 0;
			var centerY = h/2;
			var range = 50;
			var xSpeed = 1;
			var ySpeed = 0.05;
			var xPos = 0;
			var yPos = 0;
			var tempX = 0;
			var tempY = centerY;
			var shape;

			var stage = new annie.Stage('wave2',w,h,60,annie.StageScaleMode.SHOW_ALL,0);
			main();

            function main() {
            	initBackgroundLayer();
                shape = new annie.Shape();
                backgroundLayer.addChild(shape);
	            backgroundLayer.addEventListener(annie.Event.ENTER_FRAME,onframe);
            }

            function onframe() {
	            shape.beginStroke('#000000', 1);
	            shape.moveTo(tempX, tempY);
	            xPos += xSpeed;
	            angle += ySpeed;
	            yPos = centerY + Math.sin(angle) * range;
	            shape.lineTo(xPos, yPos);
	            shape.endStroke();
	            tempX = xPos;
	            tempY = yPos;

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
