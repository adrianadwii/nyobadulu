<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hi Sweetheart!</title>
    <style>
        body {
            text-align: center;
            font-family: Arial, sans-serif;
            background-color: #fff8e7;
        }
        .container {
            margin-top: 50px;
        }
        h1 {
            color: #ff4d6d;
        }
        h2 {
            color: #555;
        }
        button {
            background-color: #ff4d6d;
            color: white;
            border: none;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            border-radius: 5px;
            margin-top: 20px;
        }
        button:hover {
            background-color: #e63950;
        }
        .flower-container {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 20px;
            margin-top: 20px;
            margin-bottom: 50px;
        }
        .flower {
            width: 50px;
            height: 50px;
            position: relative;
            display: inline-block;
        }
        .petal {
            width: 20px;
            height: 20px;
            background-color: red;
            border-radius: 50%;
            position: absolute;
            animation: bloom 0.5s ease-in-out;
        }
        .petal:nth-child(1) { top: 0; left: 50%; transform: translateX(-50%); }
        .petal:nth-child(2) { bottom: 0; left: 50%; transform: translateX(-50%); }
        .petal:nth-child(3) { left: 0; top: 50%; transform: translateY(-50%); }
        .petal:nth-child(4) { right: 0; top: 50%; transform: translateY(-50%); }
        .stem {
            width: 5px;
            height: 30px;
            background-color: green;
            position: absolute;
            bottom: -30px;
            left: 50%;
            transform: translateX(-50%);
        }
        @keyframes bloom {
            from { transform: scale(0.5); opacity: 0; }
            to { transform: scale(1); opacity: 1; }
        }
        .message {
            font-size: 18px;
            color: #333;
            margin-top: 20px;
        }
        .choice-container {
            display: none;
            margin-top: 20px;
        }
        .choice-container button {
            font-size: 20px;
            margin: 10px;
            padding: 10px 30px;
        }
        #no {
            background-color: #888;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Hi Sweetheart!</h1>
        <h2>Please click me until the system says it’s done :D</h2>
        <button onclick="clickMe()">Click Me</button>
        <div class="flower-container" id="flowers"></div>
        <p class="message" id="message"></p>
        
        <div class="choice-container" id="choice">
            <p>Jadi, kamu mau nggak jadi pacar aku?</p>
            <button id="yes" onclick="sayYes()">Yes</button>
            <button id="no" onclick="resizeYes()">No</button>
        </div>
    </div>

    <script>
        let clickCount = 0;
        function clickMe() {
            clickCount++;
            let flowers = document.getElementById("flowers");
            let message = document.getElementById("message");

            if (clickCount == 1) {
                addFlower();
                message.innerText = "Eres tú kalau dalam bahasa Spanyol artinya, 'It's you.'";
            } else if (clickCount == 2) {
                addFlower();
                message.innerText = "Toda mi esperanza, eres tú, eres tú. (Seluruh harapanku, itu kamu.)";
            } else if (clickCount == 3) {
                addFlower();
                message.innerText = "Bunganya akan selalu nambah, dia nggak akan pernah layu.";
            } else if (clickCount == 4) {
                addFlower();
                message.innerText = "Seperti janji, harapan, dan kesetiaan yang selalu aku pegang.";
            } else if (clickCount == 5) {
                flowers.innerHTML = "";
                message.innerText = "Aku kangeeen banget sama kamu!";
            } else if (clickCount == 6) {
                message.innerText = "Aku pengen banget call lagi, main lagi, deket lagi...";
            } else if (clickCount == 7) {
                message.innerText = "Repotin aku untuk hal apapun, aku bersedia. Aku bakal selalu ada.";
            } else if (clickCount == 8) {
                flowers.innerHTML = "";
                for (let i = 0; i < 15; i++) addFlower();
                message.innerText = "";
                document.getElementById("choice").style.display = "block";
            }
        }

        function addFlower() {
            let flowerDiv = document.createElement("div");
            flowerDiv.classList.add("flower");

            for (let i = 0; i < 4; i++) {
                let petal = document.createElement("div");
                petal.classList.add("petal");
                flowerDiv.appendChild(petal);
            }

            let stemDiv = document.createElement("div");
            stemDiv.classList.add("stem");
            flowerDiv.appendChild(stemDiv);

            document.getElementById("flowers").appendChild(flowerDiv);
        }

        let noClickCount = 0;
        function resizeYes() {
            noClickCount++;
            let yesButton = document.getElementById("yes");
            yesButton.style.transform = `scale(${1 + noClickCount * 0.3})`;
            if (noClickCount >= 5) {
                document.getElementById("no").style.display = "none";
            }
        }

        function sayYes() {
            alert("OK, let's be together till we graduate and get married! HEHEHE");
        }
    </script>

</body>
</html>
