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

    <div>
        <div id="tsparticles"></div>
        <!-- https://github.com/matteobruni/tsparticles -->
        </div>
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

        (async () => {
          await loadHeartShape(tsParticles);
        
          await tsParticles.load("tsparticles", {
            background: {
              color: {
                value: "#301A47"
              }
            },
            particles: {
              color: {
                value: [
                  "#FFAEBC",
                  "#A0E7E5",
                  "#B4F8C8",
                  "#FBE7C6",
                  "#FFC9AE",
                  "#FFAEE5",
                  "#A0C6E7",
                  "#A0E7C2",
                  "#B4F8EA",
                  "#C2F8B4",
                  "#F4FBC6",
                  "#FBCDC6"
                ]
              },
              move: {
                angle: {
                  offset: 0,
                  value: 15
                },
                direction: "bottom",
                enable: true,
                outModes: {
                  default: "out"
                },
                speed: 3
              },
              number: {
                value: 300
              },
              opacity: {
                value: 1
              },
              shape: {
                type: "heart"
              },
              size: {
                value: 16
              },
              roll: {
                darken: {
                  enable: true,
                  value: 30
                },
                enlighten: {
                  enable: true,
                  value: 30
                },
                enable: true,
                mode: "horizontal",
                speed: {
                  min: 5,
                  max: 15
                }
              },
              zIndex: {
                value: {
                  min: 0,
                  max: 100
                },
                opacityRate: 0,
                velocityRate: 2
              }
            }
          });
        })();

    </script>
</body>
</html>
