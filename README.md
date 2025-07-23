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
      width: 75%;
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

    input[type="text"],
    input[type="file"] {
      width: 100%;
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

    input[type="text"]:focus {
      box-shadow: 0 0 8px #00eaff88;
      background-color: #2c2c2c;
    }

    input[type="file"]::-webkit-file-upload-button {
      visibility: hidden;
    }

    input[type="file"]::before {
      content: "📷 Screenshot";
      display: inline-block;
      background-color: #00eaff;
      color: #000;
      padding: 8px 14px;
      border-radius: 8px;
      cursor: pointer;
      font-weight: bold;
    }

    button {
      width: 100%;
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
    <p>Please send payment to :</p>
    <p><b>P1130580782</b></p>
    
    <form id="rechargeForm" enctype="multipart/form-data" method="POST">
      <input type="text" name="amount" placeholder="Amount (e.g. 5 USD)" required>
      <input type="text" name="wallet" placeholder="Your Payeer Wallet (e.g. P123456789)" required>
      <input type="file" name="screenshot" accept="image/*" required>

      <!-- hidden input to carry the ID from the URL -->
      <input type="hidden" name="user_id" id="user_id">

      <button type="submit">I've Sent The Payment</button>
    </form>
  </div>

  <script>
    // Get user ID from URL and set it to the hidden input
    window.onload = function() {
      const params = new URLSearchParams(window.location.search);
      const userId = params.get('id');
      if (userId) {
        document.getElementById('user_id').value = userId;
      }
    };

    const form = document.getElementById("rechargeForm");

    form.addEventListener("submit", async function(e) {
      e.preventDefault();
      const formData = new FormData(form);

      try {
        const res = await fetch("send.php", {
          method: "POST",
          body: formData
        });

        const result = await res.text();

        if (res.ok) {
          alert("✅ " + result);
          form.reset();
        } else {
          alert("❌ Error: " + result);
        }
      } catch (err) {
        alert("⚠️ حصل خطأ: " + err.message);
      }
    });
  </script>
</body>
</html>
