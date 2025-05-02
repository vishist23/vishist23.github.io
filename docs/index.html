<!DOCTYPE html>
<html>
<head>
    <title>Catch the Falling Objects</title>
    <style>
        body { margin: 0; overflow: hidden; text-align: center; font-family: Arial; }
        canvas { 
            width: 600px;
            height: 800px;
            display: block; 
            margin: 0 auto; 
            background: #f0f0f0; 
        }
        #score { font-size: 24px; margin: 10px; }
    </style>
</head>
<body>
    <div id="score">Score: 0</div>
    <canvas id="gameCanvas" width="600" height="800"></canvas>
    <script>
        // Canvas and WebGL setup
        const canvas = document.getElementById('gameCanvas');
        const gl = canvas.getContext('webgl') || canvas.getContext('experimental-webgl');
        const scoreElement = document.getElementById('score');

        if (!gl) {
            alert('WebGL not supported in your browser!');
            throw new Error('WebGL not supported');
        }

        gl.viewport(0, 0, canvas.width, canvas.height);
        gl.enable(gl.DEPTH_TEST);

        // Game state
        let score = 0;
        let gameOver = false;
        const basket = { x: 0, y: -0.8, width: 0.3, height: 0.05 };
        const objects = [];
        let objectSpeed = 0.01;

        // Initialize WebGL
        function initShaders() {
            const vsSource = `
                attribute vec2 aPosition;
                void main() {
                    gl_Position = vec4(aPosition, 0.0, 1.0);
                    gl_PointSize = 10.0;
                }
            `;
            const fsSource = `
                precision mediump float;
                uniform vec4 uColor;
                void main() {
                    gl_FragColor = uColor;
                }
            `;

            // Compile shaders
            const vertexShader = gl.createShader(gl.VERTEX_SHADER);
            gl.shaderSource(vertexShader, vsSource);
            gl.compileShader(vertexShader);

            const fragmentShader = gl.createShader(gl.FRAGMENT_SHADER);
            gl.shaderSource(fragmentShader, fsSource);
            gl.compileShader(fragmentShader);

            // Link program
            const program = gl.createProgram();
            gl.attachShader(program, vertexShader);
            gl.attachShader(program, fragmentShader);
            gl.linkProgram(program);
            gl.useProgram(program);

            return {
                program,
                aPosition: gl.getAttribLocation(program, 'aPosition'),
                uColor: gl.getUniformLocation(program, 'uColor')
            };
        }

        const shaders = initShaders();

        // Draw a rectangle
        function drawRect(x, y, width, height, color) {
            const vertices = new Float32Array([
                x, y,
                x + width, y,
                x + width, y + height,
                x, y + height
            ]);
            const indices = new Uint16Array([0, 1, 2, 0, 2, 3]);

            // Buffers
            const vertexBuffer = gl.createBuffer();
            gl.bindBuffer(gl.ARRAY_BUFFER, vertexBuffer);
            gl.bufferData(gl.ARRAY_BUFFER, vertices, gl.STATIC_DRAW);

            const indexBuffer = gl.createBuffer();
            gl.bindBuffer(gl.ELEMENT_ARRAY_BUFFER, indexBuffer);
            gl.bufferData(gl.ELEMENT_ARRAY_BUFFER, indices, gl.STATIC_DRAW);

            // Attributes
            gl.enableVertexAttribArray(shaders.aPosition);
            gl.vertexAttribPointer(shaders.aPosition, 2, gl.FLOAT, false, 0, 0);

            // Color
            gl.uniform4fv(shaders.uColor, color);

            // Draw
            gl.drawElements(gl.TRIANGLE_FAN, 4, gl.UNSIGNED_SHORT, 0);
        }

        // Spawn a new falling object
        function spawnObject() {
            objects.push({
                x: Math.random() * 1.8 - 0.9, // Random X position (-0.9 to 0.9)
                y: 1.0,
                width: 0.1,
                height: 0.1,
                color: [Math.random(), Math.random(), Math.random(), 1.0] // Random color
            });
        }

        // Check collision between basket and object
        function checkCollision(basket, obj) {
            return (
                basket.x < obj.x + obj.width &&
                basket.x + basket.width > obj.x &&
                basket.y < obj.y + obj.height &&
                basket.y + basket.height > obj.y
            );
        }

        // Mouse/touch controls
        canvas.addEventListener('mousemove', (e) => {
            const rect = canvas.getBoundingClientRect();
            basket.x = (e.clientX - rect.left) / canvas.width * 2 - 1;
        });

        // Game loop
        function gameLoop() {
            if (gameOver) return;

            // Clear screen
            gl.clearColor(0.9, 0.9, 0.9, 1.0);
            gl.clear(gl.COLOR_BUFFER_BIT | gl.DEPTH_BUFFER_BIT);

            // Draw basket (blue)
            drawRect(basket.x, basket.y, basket.width, basket.height, [0.0, 0.0, 1.0, 1.0]);

            // Spawn new objects randomly
            if (Math.random() < 0.02) {
                spawnObject();
            }

            // Update and draw objects
            for (let i = objects.length - 1; i >= 0; i--) {
                const obj = objects[i];
                obj.y -= objectSpeed;

                // Draw object
                drawRect(obj.x, obj.y, obj.width, obj.height, obj.color);

                // Check collision
                if (checkCollision(basket, obj)) {
                    objects.splice(i, 1);
                    score++;
                    scoreElement.textContent = `Score: ${score}`;
                    objectSpeed += 0.001; // Increase difficulty
                } else if (obj.y < -1.0) {
                    objects.splice(i, 1);
                    gameOver = true;
                    alert(`Game Over! Score: ${score}`);
                }
            }

            requestAnimationFrame(gameLoop);
        }

        // Start game
        gameLoop();
    </script>
</body>
</html>
