# CSS-Clock

A simple CSS clock with HTML and JavaScript. This project is designed as an introductory example of using HTML, CSS, and JavaScript together to create a functional clock.

---

## Overview

This project demonstrates how to use HTML for structure, CSS for styling, and JavaScript for dynamic functionality to make a clock that displays the current time.

## HTML Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Clock</title>
    <style>
        /* Base styling for the clock */
        .clock {
            position: relative;
            width: 200px;
            height: 200px;
            border: 10px solid #333;
            border-radius: 50%;
            background: #fff;
            margin: 20px auto;
        }

        .clock .center {
            position: absolute;
            width: 12px;
            height: 12px;
            background: #333;
            border-radius: 50%;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            z-index: 10;
        }

        /* Styling for the clock hands */
        .clock .hand {
            position: absolute;
            top: 50%;
            left: 50%;
            transform-origin: center bottom;
            transform: translate(-50%, -100%) rotate(90deg);
            transition: all 0.05s ease-in-out;
        }

        .hour { width: 8px; height: 50px; background: #333; z-index: 3; }
        .minute { width: 6px; height: 70px; background: #333; z-index: 2; }
        .second { width: 2px; height: 90px; background: red; z-index: 1; }
    </style>
</head>
<body>
    <div class="clock">
        <div class="center"></div>
        <div class="hand hour" id="hour"></div>
        <div class="hand minute" id="minute"></div>
        <div class="hand second" id="second"></div>
    </div>
    <script>
        function updateClock() {
            const now = new Date();
            const seconds = now.getSeconds();
            const minutes = now.getMinutes();
            const hours = now.getHours();

            const secondDeg = seconds * 6;
            const minuteDeg = minutes * 6 + seconds * 0.1;
            const hourDeg = hours * 30 + minutes * 0.5;

            document.getElementById("second").style.transform = `translate(-50%, -100%) rotate(${secondDeg}deg)`;
            document.getElementById("minute").style.transform = `translate(-50%, -100%) rotate(${minuteDeg}deg)`;
            document.getElementById("hour").style.transform = `translate(-50%, -100%) rotate(${hourDeg}deg)`;
        }

        setInterval(updateClock, 1000);
        updateClock();
    </script>
</body>
</html>
```
##Key Points
HTML Elements
`DOCTYPE`: Defines the document type as HTML5.
`meta` tags: Sets the character encoding to UTF-8 and adjusts the viewport for mobile scaling.
`title`: Sets "CSS Clock" as the title of the webpage.
`divs`: Creates spaces within the clock and defines structure.

##CSS Styling
`.clock`: Defines the outer circle and appearance of the clock.
`.center`: Creates a small dot at the center of the clock for aesthetic purposes.
`.hand`: Styles for the hour, minute, and second hands, including the rotation origin.

##JavaScript Logic
`updateClock()`: Calculates the angle for each hand based on the current time and applies transformations.
`const` variables store seconds, minutes, and hours, calculating the degrees for each hand.
`setInterval`: Updates the clock every second.

##Usage
To run the clock, simply open the HTML file in a browser. The JavaScript will keep the clock hands moving according to the current time.
##License
This project is open-source and free to use.
