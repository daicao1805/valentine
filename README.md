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
    <h1>Happy Valentine&#10084;</h1>
    <img src="[https://source.unsplash.com/400x300/?love,heart](https://cdn.pixabay.com/photo/2012/04/18/15/18/heart-37317_1280.png)" class="valentine-img" alt="Valentine">
    <p class="message">Chúc ngừi iu của anh có một ngày Valentine tràn đầy yêu thương!</p>
    <p class="message"> Gửi Diệp Xinh của anh muôn ngàn nụ hôn lunnnnnnnnn ạ !</p>
    <button onclick="changeMessage()">Đổi lời chúc</button>

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

        function changeMessage() {
            const messages = [
                "Chúc bạn một ngày Valentine ấm áp!",
                "Hãy luôn yêu thương và hạnh phúc nhé!",
                "Gửi đến bạn thật nhiều yêu thương!",
                "Mong rằng bạn luôn được hạnh phúc!"
            ];
            document.querySelector(".message").innerText = messages[Math.floor(Math.random() * messages.length)];
        }
    </script>
</body>
</html>
