---
layout: base
title: Background with Object
description: Use JavaScript to have an in motion background.
sprite: images/platformer/sprites/flying-ufo.png
background: images/platformer/backgrounds/alien_planet1.jpg
permalink: /background/
---
//World equals background.alien.plant.jpg
<canvas id="world"></canvas>

<script>
 console.log("UFO script loaded!");
 const keys = {};
 window.addEventListener("keydown", (e) => {
   keys[e.key] = true;
 });
 window.addEventListener("keyup", (e) => {
   keys[e.key] = false;
 });

 const canvas = document.getElementById("world");
 const ctx = canvas.getContext('2d');
 const backgroundImg = new Image();
 const spriteImg = new Image();
 backgroundImg.src = '{{page.background}}';
 spriteImg.src = '{{page.sprite}}';

 let imagesLoaded = 0;
 backgroundImg.onload = function() {
   imagesLoaded++;
   startGameWorld();
 };
 spriteImg.onload = function() {
   imagesLoaded++;
   startGameWorld();
 };

 function startGameWorld() {
   if (imagesLoaded < 2) return;
//game object is flying-ufo.png
   class GameObject {
     constructor(image, width, height, x = 0, y = 0, speedRatio = 0) {
       this.image = image;
       this.width = width;
       this.height = height;
       this.x = x;
       this.y = y;
       this.speedRatio = speedRatio;
       this.speed = GameWorld.gameSpeed * this.speedRatio;
     }
     update() {}
     draw(ctx) {
       ctx.drawImage(this.image, this.x, this.y, this.width, this.height);
     }
   }
//Background image repeats itself, through background extends--->
   class Background extends GameObject {
     constructor(image, gameWorld) {
       // Fill entire canvas
       super(image, gameWorld.width, gameWorld.height, 0, 0, 0.1);
     }
     update() {
       this.x = (this.x - this.speed) % this.width;
     }
     draw(ctx) {
       ctx.drawImage(this.image, this.x, this.y, this.width, this.height);
       ctx.drawImage(this.image, this.x + this.width, this.y, this.width, this.height);
     }
   }

   class Player extends GameObject {
     constructor(image, gameWorld) {
       const width = image.naturalWidth / 2;
       const height = image.naturalHeight / 2;
       const x = (gameWorld.width - width) / 2;
       const y = (gameWorld.height - height) / 2;
       super(image, width, height, x, y);
       //this.baseY = y;
       //this.frame = 0;
       this.speed = 5;
       console.log("Hello, UFO is flying!");
     }
     update() {
       console.log("Player.update is running without sine wave");
//Move with arrow keys using ArrowUp, ArrowDown, ArrowLeft, and ArrowRight, to move the flying-ufo.png up, down, left, right.
       // Move with arrow keys
       if (keys["ArrowUp"]) this.y -= this.speed;
       if (keys["ArrowDown"]) this.y += this.speed;
       if (keys["ArrowLeft"]) this.x -= this.speed;
       if (keys["ArrowRight"]) this.x += this.speed;

       // Keep UFO inside canvas
       if (this.x < 0) this.x = 0;
       if (this.y < 0) this.y = 0;
       if (this.x + this.width > window.innerWidth) this.x = window.innerWidth - this.width;
       if (this.y + this.height > window.innerHeight) this.y = window.innerHeight - this.height;
      
       //console.log("Hello, UFO is flying!");

       //this.y = this.baseY + Math.sin(this.frame * 0.05) * 20;
       //this.frame++;
     }
   }
//The gamworld speed controls how the object and background moves. STATIC means not moving, unlike the background and sprite (flying-ufo.png)
   class GameWorld {
     static gameSpeed = 5;
     constructor(backgroundImg, spriteImg) {
       this.canvas = document.getElementById("world");
       this.ctx = this.canvas.getContext('2d');
       this.width = window.innerWidth;
       this.height = window.innerHeight;
       this.canvas.width = this.width;
       this.canvas.height = this.height;
       this.canvas.style.width = `${this.width}px`;
       this.canvas.style.height = `${this.height}px`;
       this.canvas.style.position = 'absolute';
       this.canvas.style.left = `0px`;
       this.canvas.style.top = `${(window.innerHeight - this.height) / 2}px`;

       this.gameObjects = [
        new Background(backgroundImg, this),
        new Player(spriteImg, this)
       ];
     }
     gameLoop() {
       this.ctx.clearRect(0, 0, this.width, this.height);
       for (const obj of this.gameObjects) {
         obj.update();
         obj.draw(this.ctx);
       }
       requestAnimationFrame(this.gameLoop.bind(this));
     }
     start() {
       this.gameLoop();
     }
   }

   const world = new GameWorld(backgroundImg, spriteImg);
   world.start();
 }
