<template>
    <div class = "logo">
        <canvas id = "logocanvas" ref = "logo1" width = "1800" height = "1800"></canvas>
    </div>
</template>

<script>
    export default{
        name:'leftlogo',
        mounted:function(){
    let particleAlphabet = {
	Particle: function(x, y) {
		this.x = x;
        this.y = y;
        this.flag;
		this.radius = 3;
		this.draw = function(ctx) {
			ctx.save();
			ctx.translate(this.x, this.y);
			ctx.fillStyle = 'white';
			ctx.fillRect(0, 0, this.radius, this.radius);
			ctx.restore();
		};
	},
	init: function() {
		particleAlphabet.canvas = document.getElementById('logocanvas');
        particleAlphabet.ctx = particleAlphabet.canvas.getContext('2d');
        particleAlphabet.W = window.innerWidth/2;
        console.log(particleAlphabet.W);
        particleAlphabet.H = window.innerHeight/2;
        console.log(particleAlphabet.H);
		particleAlphabet.particlePositions = [];
		particleAlphabet.particles = [];
		particleAlphabet.tmpCanvas = document.createElement('canvas');
		particleAlphabet.tmpCtx = particleAlphabet.tmpCanvas.getContext('2d');

		particleAlphabet.canvas.width = particleAlphabet.W;
		particleAlphabet.canvas.height = particleAlphabet.H;

		particleAlphabet.flag = setInterval(function(){
			particleAlphabet.changeLetter();
			particleAlphabet.getPixels(particleAlphabet.tmpCanvas, particleAlphabet.tmpCtx);
		}, 1200);

		particleAlphabet.makeParticles(1500);
		particleAlphabet.animate();
	}, 
	currentPos: 0,
	changeLetter: function() {
		var letters = 'Easy Chat EasyChat',
			letters = letters.split(' ');
		particleAlphabet.time = letters[particleAlphabet.currentPos];
		particleAlphabet.currentPos++;
		if (particleAlphabet.currentPos >= letters.length) {
            particleAlphabet.currentPos = letters.length-1;
            clearInterval(particleAlphabet.flag)
		}
	},
	makeParticles: function(num) {
		for (var i = 0; i <= num; i++) {
			particleAlphabet.particles.push(new particleAlphabet.Particle(particleAlphabet.W / 2 + Math.random() * 100- 300, particleAlphabet.H / 2 + Math.random() * 100 -100));
		}
	},
	getPixels: function(canvas, ctx) {
		var keyword = particleAlphabet.time,
			gridX = 5,
			gridY = 5;
		canvas.width = window.innerWidth/2;
		canvas.height = window.innerHeight/2;
		ctx.fillStyle = 'white';
		ctx.font = 'italic bold 10rem Noto Serif';
		ctx.fillText(keyword, canvas.width / 2 - ctx.measureText(keyword).width / 2, canvas.height /2 );
		var idata = ctx.getImageData(0, 0, canvas.width, canvas.height);
		var buffer32 = new Uint32Array(idata.data.buffer);
		if (particleAlphabet.particlePositions.length > 0) particleAlphabet.particlePositions = [];
		for (var y = 0; y < canvas.height; y += gridY) {
			for (var x = 0; x < canvas.width; x += gridX) {
				if (buffer32[y * canvas.width + x]) {
					particleAlphabet.particlePositions.push({x: x, y: y});
				}
			}
		}
	},
	animateParticles: function() {
		var p, pPos;
		for (var i = 0, num = particleAlphabet.particles.length; i < num; i++) {
			p = particleAlphabet.particles[i];
			pPos = particleAlphabet.particlePositions[i];
			if (particleAlphabet.particles.indexOf(p) === particleAlphabet.particlePositions.indexOf(pPos)) {
			p.x += (pPos.x - p.x) * 0.5;
			p.y += (pPos.y - p.y) * 0.5;
			p.draw(particleAlphabet.ctx);
		}
		}
	},
	animate: function() {
		requestAnimationFrame(particleAlphabet.animate);
		particleAlphabet.ctx.fillStyle = 'rgb(40, 52, 60)';
		particleAlphabet.ctx.fillRect(0, 0, particleAlphabet.W, particleAlphabet.H);
		particleAlphabet.animateParticles();
	}
}
    particleAlphabet.init();
    console.log(getComputedStyle(document.getElementsByTagName("body")[0],undefined).getPropertyValue("font-size"));
        }
        }
</script>

<style lang="scss" scoped>
</style>


