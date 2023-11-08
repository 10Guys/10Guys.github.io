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
<!DOCTYPE html>
<html>
<head>
    <title>Sprite Game</title>
    <style>
        #game-container {
            position: relative;
            width: 800px;
            height: 400px;
            background-color: #eee;
        }
        .sprite {
            position: absolute;
            width: 50px;
            height: 50px;
            background-color: #ff0000;
            border: 1px solid #000;
        }
    </style>
</head>
<body>
    <div id="game-container">
        <div id="player" class="sprite"></div>
    </div>
    <script>
        // Initialize the player sprite
        const player = document.getElementById("player");
        player.style.backgroundColor = "#ff0000"; // Initial texture

        // Function to move the player sprite
        function movePlayer(event) {
            const x = event.clientX - player.clientWidth / 2;
            const y = event.clientY - player.clientHeight / 2;
            player.style.left = `${x}px`;
            player.style.top = `${y}px`;

            // Check for collision with other sprites and "delete" them
            const sprites = document.querySelectorAll(".sprite");
            sprites.forEach(sprite => {
                if (sprite !== player && isColliding(player, sprite)) {
                    sprite.remove();
                }
            });
        }

        // Function to check for collision between two elements
        function isColliding(element1, element2) {
            const rect1 = element1.getBoundingClientRect();
            const rect2 = element2.getBoundingClientRect();
            return (
                rect1.left < rect2.right &&
                rect1.right > rect2.left &&
                rect1.top < rect2.bottom &&
                rect1.bottom > rect2.top
            );
        }

        // Change the player sprite texture through a URL
        function changeTexture(textureUrl) {
            player.style.backgroundImage = `url('${textureUrl}')`;
        }

        // Add a click event to change the player's texture
        player.addEventListener("click", function() {
            const newTextureUrl = prompt("Enter the URL of a new texture image:");
            if (newTextureUrl) {
                changeTexture(newTextureUrl);
            }
        });

        // Add mousemove event to move the player
        document.addEventListener("mousemove", movePlayer);
    </script>
</body>
</html>
