# CSS3 Transitions, Animations, and Advanced JavaScript Functions

## Objectives

Create smooth CSS transitions and animations.
Use JavaScript functions for dynamic behavior.
Implement local storage for data persistence.

## Instructions
Add CSS animations to elements like buttons or images.

>[!NOTE]
> - Write a JavaScript function that:
> - Stores and retrieves user preferences using localStorage.
> - Implements an animation triggered by user actions.

## Tasks

Create a CSS animation.
Store data in localStorage.
Apply JavaScript to trigger animations.

Happy Coding! 💻✨
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Animation and localStorage</title>
    <style>
        .animated-button {
            padding: 15px 30px;
            background-color: #4CAF50;
            color: white;
            border: none;
            cursor: pointer;
            transition: transform 0.3s ease;
        }

        .animated-button.animated {
            animation: pulse 1s ease-in-out infinite alternate;
        }

        @keyframes pulse {
            from {
                transform: scale(1);
            }
            to {
                transform: scale(1.1);
            }
        }

        .animated-image {
            width: 200px;
            height: auto;
            transition: transform 0.5s ease;
        }

        .animated-image.animated {
            animation: rotate 2s linear infinite;
        }

        @keyframes rotate {
            from {
                transform: rotate(0deg);
            }
            to {
                transform: rotate(360deg);
            }
        }

    </style>
</head>
<body>

    <button class="animated-button" id="animateButton">Animate Button</button>
    <br><br>
    <img src="https://via.placeholder.com/200" alt="Animated Image" class="animated-image" id="animateImage">

    <script>
        function manageAnimations() {
            const animateButton = document.getElementById('animateButton');
            const animateImage = document.getElementById('animateImage');

            // Function to toggle animation and store preference
            function toggleAnimation(element, storageKey, animationClass) {
                const isAnimated = localStorage.getItem(storageKey) === 'true';

                if (isAnimated) {
                    element.classList.add(animationClass);
                } else {
                    element.classList.remove(animationClass);
                }

                element.addEventListener('click', () => {
                    const currentState = localStorage.getItem(storageKey) === 'true';
                    localStorage.setItem(storageKey, currentState ? 'false' : 'true');
                    element.classList.toggle(animationClass);
                });
            }

            // Apply animations and localStorage logic
            toggleAnimation(animateButton, 'buttonAnimation', 'animated');
            toggleAnimation(animateImage, 'imageAnimation', 'animated');
        }

        // Initialize animations on page load
        window.onload = manageAnimations;
    </script>

</body>
</html>
