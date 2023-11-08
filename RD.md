<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>10 Sprites Wandering and Talking</title>
    <style>
        .container {
            position: relative;
            width: 800px;
            height: 400px;
            border: 1px solid #000;
        }

        .sprite {
            position: absolute;
            width: 50px;
            height: 50px;
            background-color: #3498db;
            text-align: center;
            line-height: 50px;
            border-radius: 50%;
        }
    </style>
</head>
<body>
    <div class="container" id="container">
    </div>

    <script>
        const container = document.getElementById('container');

        // Pre-written lines for the sprites
        const lines = {
            "Sprite 1": [
                "Hello there!",
                "How are you today?",
            ],
            "Sprite 2": [
                "Hi!",
                "I'm doing great. How about you?",
            ],
            "Sprite 3": [
                "Hey!",
                "I'm good too. Thanks for asking.",
            ],
            "Sprite 4": [
                "Greetings!",
                "I'm enjoying the day.",
            ],
            "Sprite 5": [
                "Salutations!",
                "It's a beautiful day, isn't it?",
            ],
            "Sprite 6": [
                "Yo!",
                "Yes, the weather is nice.",
            ],
            "Sprite 7": [
                "Hi there!",
                "What's new with you?",
            ],
            "Sprite 8": [
                "Hello!",
                "Not much. Just wandering around.",
            ],
            "Sprite 9": [
                "Hey!",
                "Let's enjoy this moment.",
            ],
            "Sprite 10": [
                "Hi!",
                "Absolutely!",
            ],
        };

        // Create 10 sprites
        for (let i = 1; i <= 10; i++) {
            const sprite = createSprite(
                Math.random() * 750,
                Math.random() * 350,
                "Sprite " + i
            );
            container.appendChild(sprite);

            setTimeout(() => {
                wander(sprite);
                const otherSprites = Object.keys(lines).filter(name => name !== sprite.textContent);
                const randomReceiver = otherSprites[Math.floor(Math.random() * otherSprites.length)];
                talk(sprite, randomReceiver);
            }, Math.random() * 500);
        }

        function createSprite(x, y, name) {
            const sprite = document.createElement('div');
            sprite.className = 'sprite';
            sprite.style.left = x + 'px';
            sprite.style.top = y + 'px';
            sprite.textContent = name;
            return sprite;
        }

        function wander(sprite) {
            setInterval(() => {
                const newX = Math.random() * 750;
                const newY = Math.random() * 350;
                sprite.style.left = newX + 'px';
                sprite.style.top = newY + 'px';
            }, 3000);
        }

        function talk(sender, receiver) {
            const messages = lines[sender.textContent];
            if (!messages) return;

            for (let i = 0; i < messages.length; i++) {
                setTimeout(() => {
                    alert(sender.textContent + ": " + messages[i]);
                }, i * 2000);
            }
        }
    </script>
</body>
</html>
