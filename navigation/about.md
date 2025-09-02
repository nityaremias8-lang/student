---
layout: post
title: About
permalink: /about/
comments: true
---

## As a conversation Starter

Here are my origins...

<comment>
Flags are made using Wikipedia images
</comment>

<style>
 /* Cool animated gradient background */
    body {
        margin: 0;
        padding: 0;
        font-family: Arial, sans-serif;
        background: linear-gradient(-45deg, #1e3c72, #2a5298, #1e3c72, #1e90ff);
        background-size: 400% 400%;
        animation: gradientBG 15s ease infinite;
        color: white;
    }

    @keyframes gradientBG {
        0% { background-position: 0% 50%; }
        50% { background-position: 100% 50%; }
        100% { background-position: 0% 50%; }
    }

    /* Add transparency for content blocks to stand out */
    .grid-container, .image-gallery {
        background-color: rgba(0, 0, 0, 0.5);
        padding: 15px;
        border-radius: 10px;
        margin-bottom: 20px;
    }

    .grid-item {
        text-align: center;
        background-color: rgba(255, 255, 255, 0.1);
        padding: 10px;
        border-radius: 10px;
        transition: transform 0.3s, box-shadow 0.3s;
    }

    .grid-item:hover {
        transform: scale(1.05);
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
    }

    .grid-item img {
        width: 100%;
        height: 100px;
        object-fit: contain;
        border-radius: 5px;
    }

    .image-gallery {
        display: flex;
        flex-wrap: nowrap;
        overflow-x: auto;
        gap: 10px;
    }

    .image-gallery img {
        max-height: 150px;
        object-fit: cover;
        border-radius: 5px;
        transition: transform 0.3s ease;
    }

    .image-gallery img:hover {
        transform: scale(1.1);
    }

    /* Style looks pretty compact, 
       - grid-container and grid-item are referenced the code 
    */
    .grid-container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); /* Dynamic columns */
        gap: 10px;
    }
    .grid-item {
        text-align: center;
    }
    .grid-item img {
        width: 100%;
        height: 100px; /* Fixed height for uniformity */
        object-fit: contain; /* Ensure the image fits within the fixed height */
    }
    .grid-item p {
        margin: 5px 0; /* Add some margin for spacing */
    }

    .image-gallery {
        display: flex;
        flex-wrap: nowrap;
        overflow-x: auto;
        gap: 10px;
        }

    .image-gallery img {
        max-height: 150px;
        object-fit: cover;
        border-radius: 5px;
    }
</style>

<!-- This grid_container class is used by CSS styling and the id is used by JavaScript connection -->
<div class="grid-container" id="grid_container">
    <!-- content will be added here by JavaScript -->
</div>

<script>
    // 1. Make a connection to the HTML container defined in the HTML div
    var container = document.getElementById("grid_container"); // This container connects to the HTML div

    // 2. Define a JavaScript object for our http source and our data rows for the Living in the World grid
    var http_source = "https://upload.wikimedia.org/wikipedia/commons/";
    var living_in_the_world = [
        {"flag": "0/01/Flag_of_California.svg", "greeting": "Hey", "description": "California - forever"},
        {"flag": "4/41/Flag_of_India.svg", "greeting": "Hi", "description": "India"},
        {"flag": "f/f5/Flag_of_the_United_States_%281912-1959%29.svg", "greeting": "Hello", "description": "United States"},
    ];

    // 3a. Consider how to update style count for size of container
    // The grid-template-columns has been defined as dynamic with auto-fill and minmax

    // 3b. Build grid items inside of our container for each row of data
    for (const location of living_in_the_world) {
        // Create a "div" with "class grid-item" for each row
        var gridItem = document.createElement("div");
        gridItem.className = "grid-item";  // This class name connects the gridItem to the CSS style elements
        // Add "img" HTML tag for the flag
        var img = document.createElement("img");
        img.src = http_source + location.flag; // concatenate the source and flag
        img.alt = location.flag + " Flag"; // add alt text for accessibility

        // Add "p" HTML tag for the description
        var description = document.createElement("p");
        description.textContent = location.description; // extract the description

        // Add "p" HTML tag for the greeting
        var greeting = document.createElement("p");
        greeting.textContent = location.greeting;  // extract the greeting

        // Append img and p HTML tags to the grid item DIV
        gridItem.appendChild(img);
        gridItem.appendChild(description);
        gridItem.appendChild(greeting);

        // Append the grid item DIV to the container DIV
        container.appendChild(gridItem);
    }
</script>
<canvas id="confetti-canvas" style="position:fixed;top:0;left:0;width:100%;height:100%;pointer-events:none;z-index:9999;"></canvas>
<script>
  (function() {
    const canvas = document.getElementById('confetti-canvas');
    const ctx = canvas.getContext('2d');
    let W, H;
    let confettiPieces = [];

    function randomRange(min, max) {
      return Math.random() * (max - min) + min;
    }

    function ConfettiPiece() {
      this.x = randomRange(0, W);
      this.y = randomRange(-H, 0);
      this.size = randomRange(5, 10);
      this.speed = randomRange(1, 3);
      this.angle = randomRange(0, 2 * Math.PI);
      this.color = `hsl(${Math.floor(randomRange(0, 360))}, 70%, 60%)`;
      this.tilt = randomRange(-10, 10);
      this.tiltSpeed = randomRange(0.05, 0.12);
    }

    ConfettiPiece.prototype.update = function() {
      this.y += this.speed;
      this.angle += this.tiltSpeed;
      this.tilt = Math.sin(this.angle) * 15;
      if (this.y > H) {
        this.x = randomRange(0, W);
        this.y = randomRange(-20, 0);
        this.speed = randomRange(1, 3);
      }
    };

    ConfettiPiece.prototype.draw = function() {
      ctx.beginPath();
      ctx.lineWidth = this.size / 2;
      ctx.strokeStyle = this.color;
      ctx.moveTo(this.x + this.tilt, this.y);
      ctx.lineTo(this.x + this.tilt + this.size / 2, this.y + this.tilt + this.size);
      ctx.stroke();
    };

    function resizeCanvas() {
      W = window.innerWidth;
      H = window.innerHeight;
      canvas.width = W;
      canvas.height = H;
    }

    function initConfetti() {
      confettiPieces = [];
      for (let i = 0; i < 150; i++) {
        confettiPieces.push(new ConfettiPiece());
      }
    }

    function animate() {
      ctx.clearRect(0, 0, W, H);
      confettiPieces.forEach(p => {
        p.update();
        p.draw();
      });
      requestAnimationFrame(animate);
    }

    window.addEventListener('resize', resizeCanvas);

    // Initialize and start animation
    resizeCanvas();
    initConfetti();
    animate();
  })();
</script>


### Journey through Life

Here is where I went to school

- I went to Monterey Ridge Elementary School
- I went to Oak Valley Middle School 
- I go to Del Norte High School

### Culture, Family, and Fun

Everything for me, as for many others, revolves around family and friends.

- My parents are from India, but I was born in the US.
- My family is really small, I am an only child and live with both my parents.
- The gallery of pics has some of my family, fun, and from synchronized swimming.
- I love to travel

<comment>
Gallery of Pics, scroll to the right for more ...
</comment>
<div class="image-gallery">
  <img src="{{site.baseurl}}/images/about/ocean.jpeg" alt="Image 1">
  <img src="{{site.baseurl}}/images/about/sunset.jpeg" alt="Image 2">
  <img src="{{site.baseurl}}/images/about/dog.jpeg" alt="Image 3">
</div>
