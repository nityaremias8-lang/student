---
layout: base
title: Background with Object
description: Use JavaScript to have an in motion background.
# below are images for game
sprite: images/platformer/sprites/redbird.png
background: images/platformer/backgrounds/sunset.jpeg
permalink: /background
---

<!-- This is the Game World -->
<canvas id="world"></canvas>

<!-- Below is the code that makes the Game Worlds, complicated -->
<script>
  // Setting up image objects for background and player sprite
  const canvas = document.getElementById("world");
  const ctx = canvas.getContext('2d');
  // Setting up image objects
  const backgroundImg = new Image();
  const spriteImg = new Image();
  // Jekll Assignment of Images
  // Assign image sources from front matter vairables
  backgroundImg.src = '{{page.background}}'; // background image
  spriteImg.src = '{{page.sprite}}'; //Player Image
// Track loaded images and start the game once both are loaded
  let imagesLoaded = 0;
  backgroundImg.onload = function() {
    imagesLoaded++;
    startGameWorld();
  };
  /* Starts the game after images are laoded:- Creates game objects-Sets up game loop*/
  spriteImg.onload = function() {
    imagesLoaded++;
    startGameWorld();
  };

  /* This block Starts the Game
    *It checks for all images being loaded before starting
  */

  function startGameWorld() {
    if (imagesLoaded < 2) return;
    //Base class for game objects like background and player

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
    //Backgroud class scorlls the background image horizontally
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
    // Player class with floating animation using sin wave

    class Player extends GameObject {
      constructor(image, gameWorld) {
        const width = image.naturalWidth / 2;
        const height = image.naturalHeight / 2;
        const x = (gameWorld.width - width) / 2;
        const y = (gameWorld.height - height) / 2;
        super(image, width, height, x, y);
        this.baseY = y;
        this.frame = 0;
      }
      update() {
        this.y = this.baseY + Math.sin(this.frame * 0.05) * 20;
        this.frame++;
      }
    }
    //Main game controller managing canvas and gam e loop

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

        this.objects = [
         new Background(backgroundImg, this),
         new Player(spriteImg, this)
        ];
      }
      gameLoop() {
        this.ctx.clearRect(0, 0, this.width, this.height);
        for (const obj of this.objects) {
          obj.update();
          obj.draw(this.ctx);
        }
        requestAnimationFrame(this.gameLoop.bind(this));
      }
      start() {
        this.gameLoop();
      }
    }
    // Intialize and start the game world

    const world = new GameWorld(backgroundImg, spriteImg);
    world.start();
  }
