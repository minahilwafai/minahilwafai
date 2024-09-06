<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Moment Please?</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f8ff; /* Light blue background */
            font-family: 'Arial', sans-serif;
            overflow: hidden; /* Prevent scrolling */
        }

        .popup {
            text-align: center;
            background-color: #ffffff;
            border: 2px solid #ddd;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            position: relative;
            width: 90vw; /* Ensure popup fits within viewport width */
            max-width: 300px; /* Set a max-width for the popup */
            box-sizing: border-box; /* Include padding in width calculations */
        }

        .popup img {
            width: 100%; /* Scale the image to fit the popup width */
            height: auto;
            border-radius: 10px;
        }

        .question {
            font-size: 1.5em;
            margin: 20px 0;
            font-weight: bold;
            color: #ff69b4; /* Light pink color */
        }

        .buttons {
            display: flex;
            justify-content: center;
            gap: 20px; /* Increase the gap between buttons */
            position: relative;
        }

        .buttons button {
            background-color: #ff69b4; /* Light pink */
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1em;
            transition: background-color 0.3s, transform 0.3s;
            position: relative; /* Ensure button position is relative */
        }

        .buttons button:hover {
            background-color: #ff1493; /* Darker pink on hover */
        }

        .no-button {
            position: absolute; /* Absolute positioning within the popup */
            transition: transform 0.3s;
        }

        .message {
            display: none;
            font-size: 1.5em;
            font-weight: bold; /* Bold font */
            color: #ff69b4;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="popup">
        <img src="https://i.pinimg.com/736x/17/28/8d/17288d8af0fdba1156be00113059b5d0.jpg" alt="Popup Image">
        <div id="question" class="question">Do you love me?</div>
        <div class="buttons">
            <button id="yesButton">Yes</button>
            <button id="noButton" class="no-button">No</button>
        </div>
        <div id="message" class="message">I love you too, berry</div>
    </div>

    <script>
        document.getElementById('yesButton').addEventListener('click', function() {
            document.getElementById('question').style.display = 'none';
            document.getElementById('message').style.display = 'block';
            document.querySelector('.buttons').style.display = 'none'; // Hide buttons
        });

        document.getElementById('noButton').addEventListener('mouseover', function() {
            const noButton = document.getElementById('noButton');
            const popup = noButton.closest('.popup');
            const popupRect = popup.getBoundingClientRect();
            const buttonRect = noButton.getBoundingClientRect();

            // Calculate maximum possible translation within the popup
            const maxX = popupRect.width - buttonRect.width;
            const maxY = popupRect.height - buttonRect.height;

            // Define a greater movement range
            const moveFactor = 0.8; // Move up to 80% of available space

            // Generate random positions within the allowed range
            const x = Math.random() * (maxX * moveFactor);
            const y = -Math.random() * (buttonRect.height * moveFactor); // Move only up

            // Apply the translation
            noButton.style.transform = `translate(${x}px, ${y}px)`;
        });
    </script>
</body>
</html>
