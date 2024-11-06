<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JavaScript Animation</title>
    <style>
        body {
            margin: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background-color: #f0f0f0;
        }

        .box {
            width: 100px;
            height: 100px;
            background-color: #3498db;
            position: absolute;
            top: 50%; /* Center the box vertically */
            left: 0;  /* Start the box at the left side */
        }
    </style>
</head>
<body>

    <div class="box" id="box"></div>

    <script>
        // Get the box element
        const box = document.getElementById("box");

        let startTime = null;
        let position = 0; // The starting position of the box

        // Function to animate the box
        function animateBox(timestamp) {
            // The first time the function is called, store the timestamp
            if (!startTime) startTime = timestamp;

            // Calculate the time elapsed (in milliseconds)
            const progress = timestamp - startTime;

            // Move the box based on elapsed time
            position = progress / 2;  // You can adjust the speed by modifying this value

            // Apply the movement to the box (move it horizontally)
            box.style.transform = `translateX(${position}px)`;

            // Continue animating until the box reaches the right side of the screen
            if (position < window.innerWidth - 100) {
                requestAnimationFrame(animateBox); // Continue the animation
            }
        }

        // Start the animation
        requestAnimationFrame(animateBox);
    </script>

</body>
</html>
