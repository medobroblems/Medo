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
      padding: 35px 30px;
      border-radius: 20px;
      box-shadow: 0 0 20px #00eaff55;
      width: 80%;
      max-width: 420px;
    }

    form {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    h2 {
      color: #00eaff;
      text-align: center;
      font-size: 26px;
      margin-bottom: 10px;
    }

    p {
      text-align: center;
      color: #ccc;
      font-size: 15px;
      margin-bottom: 25px;
    }

    b {
      color: #fff;
    }

    input[type="text"] {
      width: 90%;
      margin-bottom: 15px;
      padding: 14px;
      border-radius: 12px;
      border: none;
      background-color: #252525;
      color: #00eaff;
      font-size: 15px;
      outline: none;
      box-shadow: inset 0 0 5px #00eaff33;
      transition: 0.3s ease;
    }

    input[name="wallet"] {
      margin-bottom: 50px;
    }

    button {
      width: 70%;
      padding: 14px;
      border-radius: 12px;
      border: none;
      background: linear-gradient(to right, #00eaff, #00b8d4);
      color: #000;
      font-weight: bold;
      font-size: 16px;
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
    <p>Please send payment to :<br></p>
    <b><p>P1130580782</p></b>
    <form id="rechargeForm">
      <input type="hidden" name="chatId" id="chatId"> <!-- لإرسال ID -->
      <input type="text" name="amount" placeholder="Amount (e.g. 5 USD)" required>
      <input type="text" name="wallet" placeholder="Your Payeer Wallet (e.g. P123456789)" required>
      <button type="submit">I've Sent The Payment</button>
    </form>
  </div>

  <script>
    // استخراج chatId من الرابط
    const urlParams = new URLSearchParams(window.location.search);
    const chatId = urlParams.get("chatId");
    if (chatId) {
      document.getElementById("chatId").value = chatId;
    }

    const form = document.getElementById("rechargeForm");
    form.addEventListener("submit", async function(e) {
      e.preventDefault();
      const formData = new FormData(form);
      try {
        const response = await fetch("https://m3dosms.darksidehost.com/aaaa/send.php", {
          method: "POST",
          body: formData
        });
        const result = await response.text();
        alert(result);
        form.reset();
      } catch (err) {
        alert("⚠️ Error: " + err.message);
      }
    });
  </script>
</body>
</html>
