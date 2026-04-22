<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="style.css">

</head>
<body>
    
    
    <div class="paper heart"></div>
    

    <div class="paper image">
      <p> my eyes have fallen </p>
      <p>in love with you </p>
      <img src="image/36a4051bf719a17619c43bf85dcccb6b.jpg" alt="memory">
    </div>

    <div class="paper image">
      <p> radhe radhe </p>
      <img src="image/457b8f8daeb11ceaf916a49cee501697.jpg" alt="radhe">
    </div>

    <div class="paper image">
      <p> radhe radhe </p>
      <img src="image/614f13428a66dcff77315eb776c10fc5.jpg" alt="radhe">
    </div>

    <div class="paper image">
      <p>radhe radhe </p>
      <img src="image/636f7b4947e9741b40954bae8856c8e6.jpg" alt="radhe">
    </div>




    <script src="script.js"></script>
</body>
</html>

let highestZ = 1;

class Paper {
    
    holdingPaper = false;

    prevMouseX = 0;
    prevMouseY = 0;

    mouseX = 0;
    mouseY = 0;

    velocityX = 0;
    velocityY = 0;

    currentPaperX = 0;
    currentPaperY = 0;
    init(element) {
        element.addEventListener('mousedown', (e) => {
            this.holdingPaper = true;
            element.style.zIndex = highestZ;
            highestZ += 1;

            if (e.button === 0) {
                this.prevMouseX = this.mouseX;
                this.prevMouseY = this.mouseY;

                console.log(this.prevMouseX);
                console.log(this.prevMouseY);
            }
        });

        document.addEventListener('mousemove', (e) => {
           this.mouseX = e.clientX;
           this.mouseY = e.clientY;

           this.velocityX = this.mouseX - this.prevMouseX;
           this.velocityY = this.mouseY - this.prevMouseY;

           if (this.holdingPaper) {
            
               this.currentPaperX += this.velocityX;
               this.currentPaperY += this.velocityY;

               this.prevMouseX = this.mouseX;
               this.prevMouseY = this.mouseY;

               element.style.transform = `translate(${this.currentPaperX}px, ${this.currentPaperY}px)`;
           }



        });
        window.addEventListener('mouseup', (e) => {
            this.holdingPaper = false;
            console.log('mouse button is released');
        });
    }
}

const papers = Array.from(document.querySelectorAll('.paper'));

papers.forEach(paperElement => {
    const p = new Paper();
    p.init(paperElement);
});

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    background-color: #f5f5f5;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background-image: url(image/322fc63a3116d41b1a98be8a2d1d34f6.jpg);
    background-size: cover;
    background-position: center;
    overflow: hidden;
}

.paper {
    position: absolute;
    background-image: url(image/ca550b01d5b66dacd10e3ae06af30b16.jpg);
    background-size: 500px;
    background-position: center;
    padding: 20px 100px;
    transform: rotateZ(-5deg);
    box-shadow: 1px 15px 20px rgba(0, 0, 0, 0.5);
    cursor: grab;
    touch-action: none;
}

.paper:active {
    cursor: grabbing;
}

.paper.heart {
    position: absolute;
    width: 200px;
    height: 200px;
    padding: 0;
    border-radius: 50%;
}
.paper.image {
    padding: 10px;
}

.paper.image p {
    font-size: 18px;
    margin: 5px 0;
}
img {
    max-height: 200px;
    width: 100%;
    user-select: none;
    display: block;
    margin-top: 10px;
    border-radius: 5px;
}
.paper.heart::after {
    content: "";
    background-image: url(image/4849b4a692049994a329c4309a6eb5f9.jpg);
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    background-size: 300px;
    background-position: center;
    background-repeat: no-repeat;
    opacity: 0.8;
}

p {
    font-family: 'Courier New', Courier, monospace;
    font-size: 50px;
    color: rgb(0, 0, 100);
    opacity: 0.75;
    user-select: none;
    line-height: 1.3;
}
