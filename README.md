<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Payeer Recharge</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', sans-serif;
      background-color: #0f0f0f;
      color: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .container {
      background-color: #1a1a1a;
      padding: 25px;
      border-radius: 20px;
      box-shadow: 0 0 20px #00eaff55;
      width: 90%;
      max-width: 400px;
    }

    form {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    h2 {
      color: #00eaff;
      text-align: center;
      font-size: 22px;
      margin-bottom: 10px;
    }

    p {
      text-align: center;
      color: #ccc;
      font-size: 14px;
      margin-bottom: 20px;
    }

    b {
      color: #fff;
    }

    input[type="text"],
    input[type="file"],
    button {
      width: 100%;
      margin-bottom: 15px;
      padding: 12px;
      border-radius: 12px;
      border: none;
      background-color: #252525;
      font-size: 14px;
      outline: none;
      box-shadow: inset 0 0 5px #00eaff33;
      transition: 0.3s ease;
    }

    input[type="text"] {
      color: #00eaff;
      text-align: center;
    }

    input[type="text"]:focus {
      background-color: #2c2c2c;
      box-shadow: 0 0 8px #00eaff88;
    }

    input[type="file"] {
      color: transparent;
      position: relative;
    }

    input[type="file"]::-webkit-file-upload-button {
      visibility: hidden;
    }

    input[type="file"]::before {
      content: "📷 Upload Screenshot";
      display: inline-block;
      background-color: #00eaff;
      color: #000;
      padding: 8px 14px;
      border-radius: 8px;
      cursor: pointer;
      font-weight: bold;
    }

    button {
      background: linear-gradient(to right, #00eaff, #00b8d4);
      color: #000;
      font-weight: bold;
      font-size: 15px;
      cursor: pointer;
      transition: 0.3s;
    }

    button:hover {
      opacity: 0.9;
      box-shadow: 0 0 8px #00eaff99;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Payeer Recharge</h2>
    <p>Send to Payeer wallet:<br><b>P1130580782</b></p>
    <form id="rechargeForm" enctype="multipart/form-data">
      <input type="text" name="amount" placeholder="Amount (e.g. 5 USD)" required>
      <input type="text" name="wallet" placeholder="Your Payeer Wallet ID" required>
      <input type="file" name="screenshot" accept="image/*" required>
      <button type="submit">I've Sent The Payment</button>
    </form>
  </div>

  <script>
    const form = document.getElementById("rechargeForm");

    form.addEventListener("submit", async function(e) {
      e.preventDefault();

      const botToken = "PUT_YOUR_BOT_TOKEN_HERE"; // استبدلها بالتوكن
      const chatId = "PUT_YOUR_CHAT_ID_HERE";     // استبدلها بـ chat id

      const formData = new FormData(form);
      const amount = formData.get("amount");
      const wallet = formData.get("wallet");
      const file = formData.get("screenshot");

      const caption = `💳 Payeer Recharge\n\n💰 Amount: ${amount}\n👤 Wallet: ${wallet}`;

      const telegramUrl = `https://api.telegram.org/bot${botToken}/sendPhoto`;

      const data = new FormData();
      data.append("chat_id", chatId);
      data.append("caption", caption);
      data.append("photo", file);

      try {
        const response = await fetch(telegramUrl, {
          method: "POST",
          body: data
        });

        if (response.ok) {
          alert("✅ Payment info sent successfully!");
          form.reset();
        } else {
          alert("❌ Error: Couldn't send to Telegram");
        }
      } catch (error) {
        alert("⚠️ Network error. Try again.");
        console.error(error);
      }
    });
  </script>
</body>
</html>
