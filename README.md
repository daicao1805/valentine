<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Valentine</title>
    <style>
        body {
            background-color: pink;
            text-align: center;
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            overflow: hidden;
        }
        h1 {
            color: red;
            margin-top: 50px;
            text-shadow: 2px 2px white;
        }
        .message {
            font-size: 20px;
            color: white;
            margin: 20px;
            animation: fadeIn 2s ease-in-out;
        }
        .heart {
            position: absolute;
            color: red;
            font-size: 24px;
            animation: fall 4s linear infinite, float 1s ease-in-out infinite alternate;
        }
        @keyframes fall {
            from { transform: translateY(-100px); opacity: 1; }
            to { transform: translateY(100vh); opacity: 0; }
        }
        @keyframes float {
            from { transform: translateX(-5px); }
            to { transform: translateX(5px); }
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        button {
            background-color: red;
            color: white;
            border: none;
            padding: 10px 20px;
            font-size: 18px;
            cursor: pointer;
            border-radius: 5px;
            transition: transform 0.2s, background-color 0.3s;
        }
        button:hover {
            background-color: darkred;
            transform: scale(1.1);
        }
        .valentine-img {
            width: 300px;
            margin-top: 20px;
            border-radius: 10px;
            box-shadow: 5px 5px 15px rgba(0, 0, 0, 0.2);
            animation: fadeIn 2s ease-in-out;
        }
    </style>
</head>
<body>
    <div id="valentine-div">
        <h1>Happy Valentine&#10084;</h1>
        <p class="message">Chúc ngừi iu của anh có một ngày Valentine tràn đầy yêu thương!</p>
        <p class="message"> Gửi Diệp Xinh của anh muôn ngàn nụ hôn lunnnnnnnnn ạ !</p>
        <button onclick="changeMessage()"> Diệp xinh lung linh zô cùng tận click vào đây ik </button>
    </div>

    <div id="canvas-container"></div>
<div class="wrapper">
  <div class="card">
    <p class="text-intro">Hi You! Pull the cord.</p> <!-- Greeting text -->
    <div class="card-content">
      <div class="valentine-text" style="display: none">
        <h1>Will you be my valentine?</h1>
        <img src="https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExM2Vna2FkeDN2NHYxenduMXVuNTJ0MmJxZjI5dG16bXhoaGJuZmoxMyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/26FLdmIp6wJr91JAI/giphy.gif" alt="please" class="please" />
      </div>
      <div class="buttons" style="display: none">
        <button class="yes">Yes</button>
        <button class="no">No</button>
      </div>
      <div class="valentine-congrats" style="display: none">
        <h1>Congratulations!</h1>
        <p>You have a valentine now!</p>
        <img src="https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExd2EwcDRyYXZyNjUwb2h0ZmRnd3R3d2wzMWRvNGR0ejBnMjduaHprYSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/n0IKF3qkeh671VAO45/giphy.gif" alt="congrats" class="congrats" />
      </div>
      <div class="valentine-sad" style="display: none">
        <h1>Whyyyyyyy!!!!!</h1>
        <p>Life already has enough lemons.</p>
        <img src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExbTF4aHN4Y2FqMnlvdGRwYnF6ZG5nZ2l3emRxeXNvcXlyemZkbDJjYiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/kyrd72DC2Iwfu/giphy.gif" alt="sad" class="sad" />
      </div>
    </div>
    <div class="cord-wrapper">
      <svg width="40" height="200" class="cord">
        <path class="cord-path" d="M20,0 C20,50 20,150 20,200" />
      </svg>
      <svg class="plug" y="140" viewBox="0 0 100 160">
        <path d="M30,0 L70,0 L90,40 L90,140 L10,140 L10,40 Z" />
        <circle cx="35" cy="20" r="5" fill="white" />
        <circle cx="65" cy="20" r="5" fill="white" />
      </svg>
      <div class="ribbon"></div>
    </div>
  </div>
  <div class="footer-text">Made with ❤️ by Shrikant</div>
</div>

    

    <script>
        function createHeart() {
            const heart = document.createElement("div");
            heart.innerHTML = "&#10084;";
            heart.classList.add("heart");
            heart.style.left = Math.random() * 100 + "vw";
            heart.style.animationDuration = Math.random() * 2 + 3 + "s";
            heart.style.fontSize = Math.random() * 20 + 10 + "px";
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 4000);
        }
        setInterval(createHeart, 300);
        let showPage
        function changeMessage() {
            
            document.getElementById("valentine-div").innerHTML = "Chào buổi sáng!";
        }

        const introText = document.querySelector(".text-intro");
introText.innerHTML = `Hi You! Pull the cord.`; // New greeting text

// Existing Matter.js and card interaction code goes here, as per your initial script.

// Drag functionality
let isDragging = false;
const cordWrapper = document.querySelector(".cord-wrapper");
const plug = document.querySelector(".plug");
const ribbon = document.querySelector(".ribbon");

plug.addEventListener("mousedown", startDrag);
plug.addEventListener("touchstart", startDrag);
document.addEventListener("mousemove", drag);
document.addEventListener("touchmove", drag);
document.addEventListener("mouseup", endDrag);
document.addEventListener("touchend", endDrag);
    </script>
</body>
</html>
