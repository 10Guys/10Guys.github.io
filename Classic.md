<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Changing Texture Sprites</title>
    <style>
        .sprite {
            width: 50px;
            height: 50px;
            background-size: cover;
            position: absolute;
        }
    </style>
</head>
<body>
    <script>
        function getRandomPosition() {
            const x = Math.random() * (window.innerWidth - 50);
            const y = Math.random() * (window.innerHeight - 50);
            return { x, y };
        }

        function setRandomTexture(sprite) {
            const imageUrl = 'https://media.tenor.com/nZQlCgAcIXQAAAAi/hood-irony-ghetto-smosh.gif'; // Replace with the URL of your image
            sprite.style.backgroundImage = `url(${imageUrl})`;
        }

        function moveSprite(sprite) {
            const newPosition = getRandomPosition();
            sprite.style.left = newPosition.x + 'px';
            sprite.style.top = newPosition.y + 'px';
            setRandomTexture(sprite);
        }

        // Create 10 sprites and initialize their position and texture
        const sprites = [];
        for (let i = 0; i < 10; i++) {
            const sprite = document.createElement('div');
            sprite.className = 'sprite';
            document.body.appendChild(sprite);
            sprites.push(sprite);
            moveSprite(sprite);
        }

        // Move each sprite and change texture every 2 seconds (adjust as needed)
        setInterval(() => {
            sprites.forEach((sprite) => {
                moveSprite(sprite);
            });
        }, 2000);
    </script>
</body>
</html>
