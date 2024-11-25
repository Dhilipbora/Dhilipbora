<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FLAMES Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 20px;
            background-color: #f2f2f2;
        }
        h1 {
            color: #ff6347;
        }
        input, button {
            margin: 10px;
            padding: 10px;
            font-size: 16px;
        }
        .result {
            margin-top: 20px;
            font-size: 20px;
            color: #2e8b57;
        }
    </style>
</head>
<body>
    <h1>FLAMES Game</h1>
    <p>Enter two names to find their relationship:</p>
    <input type="text" id="name1" placeholder="Your Name">
    <input type="text" id="name2" placeholder="Their Name">
    <button onclick="calculateFlames()">Find Relationship</button>
    <div class="result" id="result"></div>

    <script>
        function calculateFlames() {
            const name1 = document.getElementById('name1').value.toLowerCase().replace(/\s+/g, '');
            const name2 = document.getElementById('name2').value.toLowerCase().replace(/\s+/g, '');

            if (!name1 || !name2) {
                document.getElementById('result').innerText = 'Please enter both names.';
                return;
            }

            let combined = name1 + name2;
            let uniqueCount = combined.length;

            for (let char of name1) {
                if (name2.includes(char)) {
                    uniqueCount -= 2; // Remove matching pairs
                    name2 = name2.replace(char, '');
                }
            }

            const flames = ['Friends', 'Lovers', 'Affectionate', 'Marriage', 'Enemies', 'Siblings'];
            const resultIndex = uniqueCount % flames.length;

            document.getElementById('result').innerText = 
                `The relationship is: ${flames[resultIndex] || 'Unknown'}`;
        }
    </script>
</body>
</html>
