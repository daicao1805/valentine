<html lang="vi">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Happy Valentine</title>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/matter-js/0.19.0/matter.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
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
      from {
        transform: translateY(-100px);
        opacity: 1;
      }

      to {
        transform: translateY(100vh);
        opacity: 0;
      }
    }

    @keyframes float {
      from {
        transform: translateX(-5px);
      }

      to {
        transform: translateX(5px);
      }
    }

    @keyframes fadeIn {
      from {
        opacity: 0;
      }

      to {
        opacity: 1;
      }
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

    .heart1 {
      position: absolute;
      color: red;
      font-size: 20px;
      animation: fall linear infinite;
    }

    @keyframes fall {
      0% {
        transform: translateY(-10vh) rotate(0deg);
        opacity: 1;
      }

      100% {
        transform: translateY(100vh) rotate(360deg);
        opacity: 0;
      }
    }

    #canvas-container {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 1;
    }

    .wrapper {
      position: relative;
      width: 100vw;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: url("https://images.unsplash.com/photo-1503455637927-730bce8583c0?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D");
      background-repeat: no-repeat;
      background-size: cover;
    }

    .heart2 {
      --c: red;
      width: 200px;
      aspect-ratio: 1;
      background: radial-gradient(at 70% 31%, var(--c) 29%, #0000 30%),
        radial-gradient(at 30% 31%, var(--c) 29%, #0000 30%),
        conic-gradient(from -45deg at 50% 84%, var(--c) 90deg, #0000 0) bottom/100% 50% no-repeat;
    }

    .card {
      position: relative;
      width: 300px;
      height: 400px;
      background: white;
      border-radius: 15px;
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
      transform-origin: top;
      transform-style: preserve-3d;
      transition: transform 0.5s ease;
    }

    img {
      border-radius: 8px;
    }

    .card-content {
      padding: 10px;
      opacity: 0;
      transition: opacity 0.3s;
      text-align: center;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
    }

    .card.open {
      transform: rotateX(0deg);
    }

    .card.open .card-content {
      opacity: 1;
    }

    .cord-wrapper {
      position: absolute;
      top: -100px;
      left: 50%;
      transform: translateX(-50%);
      width: 40px;
      height: 200px;
      cursor: grab;
    }

    .plug {
      position: absolute;
      bottom: 0;
      left: 0;
      width: 40px;
      height: 60px;
      fill: #fe3a65;
      cursor: grab;
      transform: translateY(140px);
      transform-origin: 50% 0%;
      z-index: 20;
    }

    .plug:active {
      cursor: grabbing;
    }

    .ribbon {
      position: absolute;
      top: 0;
      left: 50%;
      width: 8px;
      height: 100%;
      transform-origin: top;
      transform: translateX(-50%);
    }

    .valentine-text {
      font-size: 24px;
      margin-bottom: 20px;
      color: #fe3a65;
    }

    h1 {
      font-size: 32px;
      color: #fe3a65;
      margin-bottom: 20px;
    }

    .valentine-congrats h1,
    .valentine-sad h1 {
      margin-bottom: 0px;
    }

    .please,
    .congrats,
    .sad {
      width: 280px;
      /* height: 50px; */
    }

    .buttons {
      display: flex;
      flex-wrap: nowrap;
      flex-direction: row;
      justify-content: center;
      gap: 12px;
    }

    .buttons button {
      padding: 10px 20px;
      font-size: 16px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      width: 130px;
      transition: transform 0.2s ease;
    }

    .buttons button.yes {
      background-color: #4caf50;
      color: white;
    }

    .buttons button.no {
      background-color: #f44336;
      color: white;
    }

    .text-intro {
      color: black;
      position: absolute;
      bottom: -40px;
      font-size: 20px;
      text-transform: capitalize;
      font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
    }

    .footer-text {
      position: absolute;
      bottom: 10px;
      left: 50%;
      transform: translateX(-50%);
      font-size: 30px;
      color: white;
    }

    #iwant {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
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

  <div id="iwant">
    <div id="canvas-container"></div>
    <div class="wrapper">
      <div class="card">
        <p class="text-intro"></p>
        <div class="card-content">
          <!-- <div class="heart"></div> -->
          <div class="valentine-text" style="display: none">
            <h1>Iu anh nhìu nhìu nhé bây bi?</h1>
            <img
              src="https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExM2Vna2FkeDN2NHYxenduMXVuNTJ0MmJxZjI5dG16bXhoaGJuZmoxMyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/26FLdmIp6wJr91JAI/giphy.gif"
              alt="please" class="please" />
          </div>
          <div class="buttons" style="display: none">
            <button class="yes">tất nhin rùi</button>
            <button class="no">khum đc No</button>
          </div>
          <div class="valentine-congrats" style="display: none">
            <h1>chúc mừng ngừi iu!</h1>
            <p>You have a valentine now!</p>
            <img
              src="https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExd2EwcDRyYXZyNjUwb2h0ZmRnd3R3d2wzMWRvNGR0ejBnMjduaHprYSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/n0IKF3qkeh671VAO45/giphy.gif"
              alt="congrats" class="congrats" />
          </div>
          <div class="valentine-sad" style="display: none">
            <h1>Whyyyyyyy!!!!!</h1>
            <p>Life already has enough lemons.</p>
            <img
              src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExbTF4aHN4Y2FqMnlvdGRwYnF6ZG5nZ2l3emRxeXNvcXlyemZkbDJjYiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/kyrd72DC2Iwfu/giphy.gif"
              alt="sad" class="sad" />
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
    </div>
  </div>
  <div class="footer-text">Trọng Đại ❤️ Ngọc Diệp</div>

  <script>
    function createHeart1() {
      const heart = document.createElement("div");
      heart.innerHTML = "&#10084;";
      heart.classList.add("heart1");
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.animationDuration = Math.random() * 2 + 3 + "s";
      heart.style.fontSize = Math.random() * 20 + 10 + "px";
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 4000);
    }
    setInterval(createHeart, 300);
    let showPage
    function changeMessage() {

      document.getElementById("valentine-div").innerHTML = `<h1>I Love U chụt chụt!</h1> <button onclick="changeMessage2()"> Diệp xinh lung linh zô cùng tận click vào đây tiếp ik mò</button>
`;
      setInterval(createHeart1, 300);
    }

    function createHeart() {
      const heart = document.createElement("div");
      heart.innerHTML = "❤️";
      heart.classList.add("heart");
      document.body.appendChild(heart);

      const size = Math.random() * 20 + 10; // Kích thước ngẫu nhiên
      heart.style.fontSize = `${size}px`;

      heart.style.left = Math.random() * 100 + "vw"; // Vị trí ngang ngẫu nhiên
      heart.style.animationDuration = Math.random() * 3 + 2 + "s"; // Thời gian rơi ngẫu nhiên

      setTimeout(() => {
        heart.remove();
      }, 5000);
    }
    function changeMessage2() {
      document.getElementById("valentine-div").innerHTML = ``;
      document.getElementById("iwant").style.display = "block"
    }

    // const urlParams = new URLSearchParams(window.location.search);
    // const name = urlParams.get("k"); // Get the value of "name"
    const introText = document.querySelector(".text-intro");
    introText.innerHTML = `Hello Diệp xinh của a. kéo xún ik`;
    const engine = Matter.Engine.create();
    const world = engine.world;

    const render = Matter.Render.create({
      element: document.getElementById("canvas-container"),
      engine: engine,
      options: {
        width: window.innerWidth,
        height: window.innerHeight,
        wireframes: false,
        background: "transparent"
      }
    });

    // Create a chain of points for the ribbon
    const segments = 10;
    const segmentHeight = 150 / segments;
    const points = [];
    const constraints = [];

    // Get card position
    const card = document.querySelector(".card");
    const cardRect = card.getBoundingClientRect();
    const startX = window.innerWidth / 2;
    const startY = cardRect.top;

    // Create points
    for (let i = 0; i <= segments; i++) {
      const point = Matter.Bodies.circle(startX, startY + i * segmentHeight, 2, {
        friction: 0.5,
        restitution: 0.5,
        isStatic: i === 0,
        render: {
          visible: true,
          fillStyle: "#000000",
          strokeStyle: "#000000"
        }
      });
      points.push(point);
      Matter.World.add(world, point);
    }

    // Connect points with constraints
    for (let i = 0; i < points.length - 1; i++) {
      const constraint = Matter.Constraint.create({
        bodyA: points[i],
        bodyB: points[i + 1],
        stiffness: 0.1,
        damping: 0.05,
        length: segmentHeight,
        render: {
          visible: true,
          strokeStyle: "#fe3a65",
          lineWidth: 1
        }
      });
      constraints.push(constraint);
      Matter.World.add(world, constraint);
    }

    // Create and start the runner
    const runner = Matter.Runner.create();
    Matter.Runner.run(runner, engine);
    Matter.Render.run(render);

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

    function startDrag(e) {
      e.preventDefault(); // Prevent default touch behavior
      isDragging = true;
      plug.style.cursor = "grabbing";
    }

    function drag(e) {
      if (!isDragging) return;

      // Get client coordinates for both mouse and touch events
      const clientX = e.clientX || e.touches[0].clientX;
      const clientY = e.clientY || e.touches[0].clientY;

      const lastPoint = points[points.length - 1];
      Matter.Body.setPosition(lastPoint, {
        x: clientX,
        y: clientY
      });

      // Update ribbon visuals
      updateRibbon();

      // Check if pulled far enough to open
      if (clientY > cardRect.top + 300 && !card.classList.contains("open")) {
        openCard();
      }
    }

    function updateRibbon() {
      const segments = points.length;

      for (let i = 0; i < segments - 1; i++) {
        const current = points[i];
        const next = points[i + 1];

        const dx = next.position.x - current.position.x;
        const dy = next.position.y - current.position.y;
        const angle = Math.atan2(dy, dx);

        const segmentLength = Math.sqrt(dx * dx + dy * dy);
        gsap.set(ribbon, {
          height: segmentLength,
          rotation: angle * (180 / Math.PI),
          x: current.position.x - startX,
          y: current.position.y - startY
        });

        // Update plug position and rotation
        if (i === segments - 2) {
          gsap.set(plug, {
            x: next.position.x - startX, // Center the plug
            y: next.position.y - startY - 20, // Offset to align with ribbon
            rotation: angle * (180 / Math.PI) - 90, // Fix rotation
            transformOrigin: "50% 0%"
          });
        }
      }
    }

    function endDrag() {
      isDragging = false;
      plug.style.cursor = "grab";
    }

    function openCard() {
      card.classList.add("open");

      // Shock effect (vibration)
      gsap.to(card, {
        y: "+=30",
        yoyo: true,
        repeat: 5,
        duration: 0.05,
        onComplete: () => {
          gsap.set(card, { x: 0 }); // Reset position after vibration
        }
      });

      // Confetti effect
      confetti({
        particleCount: 300,
        spread: 100,
        origin: { y: 0.6 }
      });

      // Morph plug
      gsap.to(".plug path", {
        duration: 0.5,
        attr: { d: "M30,0 L70,0 L85,30 L85,120 L15,120 L15,30 Z" },
        ease: "power2.inOut"
      });

      // Show content
      gsap.to(".card-content", {
        opacity: 1,
        duration: 0.5,
        delay: 0.3
      });

      // Show valentine text and buttons
      gsap.to(".valentine-text, .buttons", {
        display: "block",
        opacity: 1,
        duration: 0.5,
        delay: 0.5
      });

      // Hide ribbon and cord
      gsap.to([cordWrapper, ribbon], {
        opacity: 0,
        duration: 0.5,
        onComplete: () => {
          cordWrapper.style.display = "none";
          ribbon.style.display = "none";
        }
      });

      const tl = new gsap.timeline();
      tl.to(".card", { rotateX: -10, duration: 0.2 })
        .to(".card", { rotateX: 0, duration: 0.1 })
        .to(".card", { rotateX: 10, duration: 0.14 })
        .to(".card", { rotateX: 0, duration: 0.05 })
        .repeat(2);

      gsap.to(".text-intro", {
        opacity: 0,
        duration: 0.5,
        onComplete: () => {
          introText.style.display = "none";
        }
      });

      // Hide Matter.js points and constraints
      points.forEach((point) => {
        point.render.visible = false;
      });
      constraints.forEach((constraint) => {
        constraint.render.visible = false;
      });
    }

    // Add event listeners for buttons
    const yesButton = document.querySelector(".buttons .yes");
    const noButton = document.querySelector(".buttons .no");

    yesButton.addEventListener("click", () => {
      const tl = new gsap.timeline();
      gsap.to(".valentine-text, .buttons", {
        display: "none",
        opacity: 0,
        duration: 0.5
      });
      gsap.to(".valentine-congrats", {
        display: "block",
        opacity: 1,
        duration: 0.5,
        delay: 0.5
      });
      tl.to(".card", {
        width: window.innerWidth < 420 ? window.innerWidth : 800,
        height: 540,
        duration: 1,
        ease: "power2.in"
      }).to(".congrats, .valentine-congrats", {
        width: "100%",
        height: "100%",
        duration: 1
      });

      confetti({
        particleCount: 500,
        spread: 150,
        origin: { y: 0.6 }
      });
      setInterval(() => {
        confetti({
          particleCount: 500,
          spread: 150,
          origin: { y: 0.6 }
        });
      }, 5000);
    });

    noButton.addEventListener("click", () => {
      const tl = new gsap.timeline();
      gsap.to(".valentine-text, .buttons", {
        display: "none",
        opacity: 0,
        duration: 0.5
      });
      gsap.to(".valentine-sad", {
        display: "block",
        opacity: 1,
        duration: 0.5,
        delay: 0.5
      });
      tl.to(".card", {
        width: window.innerWidth < 420 ? window.innerWidth : 800,
        height: 540,
        duration: 1,
        ease: "power2.in"
      });
      tl.to(".valentine-sad", {
        width: "100%",
        height: "100%",
        duration: 0.3
      });
      tl.to(".sad", {
        width: "90%",
        height: "100%",
        duration: 0.7
      });

      // confetti({
      //     particleCount: 500,
      //     spread: 150,
      //     origin: { y: 0.6 },
      // });
      // setInterval(() => {
      //     confetti({
      //         particleCount: 500,
      //         spread: 150,
      //         origin: { y: 0.6 },
      //     });
      // }, 5000);
    });

    noButton.addEventListener("mouseover", () => {
      const minDisplacement = 100; // Minimum move distance
      const maxDisplacement = 500; // Maximum move distance

      const getRandomDisplacement = (min, max) => {
        let displacement = Math.random() * (max - min) + min;
        return Math.random() < 0.5 ? -displacement : displacement;
      };

      const buttonRect = noButton.getBoundingClientRect();
      const viewportWidth = window.innerWidth - buttonRect.width;
      const viewportHeight = window.innerHeight - buttonRect.height;

      let x = getRandomDisplacement(minDisplacement, maxDisplacement);
      let y = getRandomDisplacement(minDisplacement, maxDisplacement);

      // Ensure button stays within screen boundaries
      if (buttonRect.left + x < 0) x = Math.abs(x); // Prevent moving past left boundary
      if (buttonRect.right + x > viewportWidth) x = -Math.abs(x); // Prevent moving past right boundary
      if (buttonRect.top + y < 0) y = Math.abs(y); // Prevent moving past top boundary
      if (buttonRect.bottom + y > viewportHeight) y = -Math.abs(y); // Prevent moving past bottom boundary

      gsap.to(noButton, {
        x: `+=${x}`, // Move relative to current position
        y: `+=${y}`,
        duration: 0.1,
        delay: 0.2,
        ease: "power2.out"
      });
    });

    // Update ribbon on animation frame
    function animate() {
      updateRibbon();
      requestAnimationFrame(animate);
    }
    animate();

    // Initial card setup
    gsap.set(".card", {
      rotateX: 0,
      transformPerspective: 1000
    });



  </script>
</body>

</html>
