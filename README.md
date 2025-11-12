# Tell-Me-the-Meaning-of-My-Name-
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Tell Me the Meaning of My Name</title>

  <!-- 🔸 PLACE YOUR GOOGLE ADSENSE GLOBAL SCRIPT HERE -->
  <!-- Example (replace with your own after approval):
  <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-XXXXXXXXXXXX"
          crossorigin="anonymous"></script>
  -->

  <style>
    body {
      font-family: "Poppins", sans-serif;
      background: linear-gradient(135deg, #74ABE2, #5563DE);
      text-align: center;
      padding: 40px;
      color: #fff;
      overflow-x: hidden;
    }

    h1 {
      font-size: 2.5em;
      margin-bottom: 20px;
      animation: fadeInDown 1.5s ease;
    }

    @keyframes fadeInDown {
      from { opacity: 0; transform: translateY(-30px); }
      to { opacity: 1; transform: translateY(0); }
    }

    input {
      padding: 10px;
      font-size: 1em;
      width: 250px;
      border-radius: 10px;
      border: none;
      margin-top: 10px;
      text-align: center;
    }

    button {
      padding: 10px 20px;
      font-size: 1em;
      background-color: #00c6ff;
      border: none;
      border-radius: 10px;
      color: white;
      cursor: pointer;
      margin-left: 10px;
      transition: 0.3s;
    }

    button:hover {
      background-color: #0072ff;
      transform: scale(1.05);
    }

    .result {
      margin-top: 30px;
      font-size: 1.2em;
      background: rgba(255,255,255,0.9);
      color: #333;
      display: inline-block;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.2);
      min-width: 300px;
      animation: fadeIn 1s ease;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: scale(0.95); }
      to { opacity: 1; transform: scale(1); }
    }

    .ad-box {
      margin-top: 30px;
      background: rgba(255,255,255,0.8);
      padding: 15px;
      border-radius: 8px;
      color: #000;
    }

    footer {
      margin-top: 50px;
      font-size: 0.9em;
      color: #eee;
    }
  </style>
</head>
<body>
  <h1>🔤 Tell Me the Meaning of My Name</h1>
  <p>Type your name below to discover its meaning and origin!</p>

  <!-- 🔸 TOP AD SECTION -->
  <div class="ad-box">
    <p>🪧 Advertisement Space (Top)</p>
    <!-- Paste your AdSense ad code here -->
  </div>

  <input type="text" id="nameInput" placeholder="Enter your name">
  <button onclick="getMeaning()">Find Meaning</button>

  <div class="result" id="resultBox">✨ Waiting for your name...</div>

  <!-- 🔸 MIDDLE AD SECTION -->
  <div class="ad-box">
    <p>🪧 Advertisement Space (Middle)</p>
    <!-- Paste your AdSense ad code here -->
  </div>

  <footer>
    <p>Created by <strong>Gurmeet Singh</strong> | 📧 your@email.com</p>
  </footer>

  <script>
    async function getMeaning() {
      const name = document.getElementById("nameInput").value.trim();
      const resultBox = document.getElementById("resultBox");

      if (!name) {
        resultBox.innerHTML = "⚠️ Please enter a name.";
        return;
      }

      resultBox.innerHTML = "🔍 Searching meaning for \"" + name + "\"...";

      try {
        const response = await fetch(`https://api.api-ninjas.com/v1/babynames?name=${name}`, {
          headers: { 'X-Api-Key': 'demo' } // Replace with your own API key
        });

        if (!response.ok) throw new Error("Not found");

        const data = await response.json();
        if (data.length > 0 && data[0].meaning) {
          resultBox.innerHTML = `<strong>${name}:</strong> ${data[0].meaning}`;
        } else {
          resultBox.innerHTML = `❓ Sorry, I couldn’t find a meaning for "<strong>${name}</strong>".`;
        }
      } catch (error) {
        resultBox.innerHTML = `❌ Error: Could not fetch meaning.`;
      }
    }
  </script>
</body>
</html>
