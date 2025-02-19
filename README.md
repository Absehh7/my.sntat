<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>كاش فور</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
            text-align: center;
            overflow: hidden;
        }
        header {
            background-color: #4CAF50;
            color: white;
            padding: 3px;
            font-size: 12px;
            position: relative;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 5px 10px;
        }
        header h1 {
            margin: 0;
            font-size: 16px;
        }
        .balance {
            background-color: #fff;
            padding: 5px 10px;
            border-radius: 5px;
            box-shadow: 0px 0px 5px rgba(0,0,0,0.1);
            font-size: 14px;
        }
        .container {
            width: 100%;
            margin: 20px auto;
            max-width: 1200px;
        }
        .products {
            display: flex;
            flex-direction: row;
            justify-content: flex-start;
            overflow-x: auto;
            padding: 10px 0;
        }
        .product {
            background-color: #fff;
            border-radius: 5px;
            box-shadow: 0px 0px 5px rgba(0,0,0,0.1);
            margin: 0 10px;
            flex: 0 0 auto;
            width: 160px;
            padding: 10px;
            text-align: center;
        }
        .product img {
            max-width: 100%;
            height: auto;
            border-radius: 5px;
        }
        .product span {
            display: block;
            margin-top: 10px;
            font-size: 16px;
            color: #555;
        }
        #purchaseModal, #codeModal, #accountModal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            justify-content: center;
            align-items: center;
        }
        .modal-content {
            background-color: #fff;
            padding: 20px;
            border-radius: 5px;
            width: 90%;
            max-width: 400px;
            text-align: left;
        }
        .close {
            float: right;
            font-size: 18px;
            cursor: pointer;
        }
        .modal-content label {
            display: block;
            margin-bottom: 10px;
        }
        .modal-content input[type="text"], .modal-content input[type="password"] {
            width: 100%;
            padding: 8px;
            margin-bottom: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .modal-content button {
            width: 48%;
            padding: 10px;
            background-color: #4CAF50;
            border: none;
            color: white;
            font-size: 16px;
            border-radius: 5px;
            cursor: pointer;
            margin-right: 4%;
        }
        .modal-content button:hover {
            background-color: #45a049;
        }
        .cancel-button {
            background-color: #f44336;
        }
        .cancel-button:hover {
            background-color: #e53935;
        }
        #profileIcon {
            font-size: 20px;
            cursor: pointer;
        }
        .refresh-container {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background-color: #4CAF50;
            cursor: pointer;
        }
    </style>
</head>
<body>

<header>
    <h1>كاش فور</h1>
    <div class="balance" id="headerBalance" onclick="openCodeModal()">
        <span>الرصيد: <span id="balanceAmount">0</span> دينار</span>
    </div>
    <div id="profileIcon" onclick="openAccountModal()">👤</div>
</header>

<div class="refresh-container" onclick="refreshPage()"></div>

<div class="container">
    <div class="products">
        <!-- تأكد من أن جميع الصور ظاهرة بشكل صحيح -->
        <div class="product" onclick="purchase('شدات بوبجي 30', 1500)">
            <img src="https://imgur.com/VXSLu2o.jpg" alt="شدات بوبجي 30">
            <span>1000 دينار عراقي</span>
        </div>
        <div class="product" onclick="purchase('شدات بوبجي 2000', 2000)">
            <img src="https://imgur.com/0JwgVvK.jpg" alt="شدات بوبجي 2000">
            <span>2000 دينار عراقي</span>
        </div>
        <div class="product" onclick="purchase('شدات بوبجي 4000', 4000)">
            <img src="https://imgur.com/3eW0fsx.jpg" alt="شدات بوبجي 4000">
            <span>4000 دينار عراقي</span>
        </div>
        <div class="product" onclick="purchase('شدات بوبجي 6000', 6000)">
            <img src="https://imgur.com/a79xaRT.jpg" alt="شدات بوبجي 6000">
            <span>6000 دينار عراقي</span>
        </div>
        <div class="product" onclick="purchase('شدات بوبجي 8000', 8000)">
            <img src="https://imgur.com/zCJOrbV.jpg" alt="شدات بوبجي 8000">
            <span>8000 دينار عراقي</span>
        </div>
        <div class="product" onclick="purchase('شدات بوبجي 9000', 9000)">
            <img src="https://i.imgur.com/8uo65JP.jpeg" alt="شدات بوبجي 9000">
            <span>9000 دينار عراقي</span>
        </div>
        <div class="product" onclick="purchase('شدات بوبجي 1000', 1000)">
            <img src="https://i.imgur.com/2YDVjcz.jpeg" alt="شدات بوبجي 1000">
            <span>10000 دينار عراقي</span>
        </div>
        <div class="product" onclick="purchase('شدات بوبجي 16000', 16000)">
            <img src="https://i.imgur.com/SICyKMC.jpeg" alt="شدات بوبجي 16000">
            <span>16000 دينار عراقي</span>
        </div>
        <div class="product" onclick="purchase('شدات بوبجي 26000', 26000)">
            <img src="https://i.imgur.com/QdHVQjK.jpeg" alt="شدات بوبجي 26000">
            <span>26000 دينار عراقي</span>
        </div>
    </div>
</div>

<!-- Modal for purchase -->
<div id="purchaseModal" class="modal">
    <div class="modal-content">
        <span class="close" onclick="closeModal()">&times;</span>
        <h2>تأكيد الشراء</h2>
        <p id="productName"></p>
        <p id="productPrice"></p>
        <label for="userID">أدخل ID المستخدم:</label>
        <input type="text" id="userID" placeholder="ID">
        <label for="username">أدخل اسم المستخدم داخل اللعبة:</label>
        <input type="text" id="username" placeholder="اسم المستخدم">
        <button onclick="confirmPurchase()">تأكيد</button>
        <button class="cancel-button" onclick="closeModal()">إلغاء</button>
    </div>
</div>

<!-- Modal for adding code -->
<div id="codeModal" class="modal">
    <div class="modal-content">
        <span class="close" onclick="closeModal()">&times;</span>
        <h2>إضافة كود شحن</h2>
        <label for="codeInput">أدخل الكود:</label>
        <input type="text" id="codeInput" placeholder="كود الشحن">
        <button onclick="applyCode()">تطبيق</button>
    </div>
</div>

<!-- Modal for account info -->
<div id="accountModal" class="modal">
    <div class="modal-content">
        <span class="close" onclick="closeModal()">&times;</span>
        <h2>معلومات الحساب</h2>
        <label for="newUsername">اسم المستخدم:</label>
        <input type="text" id="newUsername" placeholder="اسم المستخدم">
        <button onclick="saveUsername()">حفظ اسم المستخدم</button>
    </div>
</div>

<script>
    let balance = 0;
    let selectedProduct = '';
    let selectedPrice = 0;
    const validCodes = ['F857SB5', 'FOS0D62', 'GZE3621', 'ABS417E', 'GMEQK4', '17EBSYN', 'H27RIXB', 'VZJN26X', '52NXY2N', 'YZNDVL2', 'VXT184M', '5W84B2Y', 'VA52ME8', '6WIEB3IW', '25E715EU', '5W738RY', '2YEU6WI', '37CORNU', '273BNOQ', '638FEPN', '4ME66Y8', 'TQER999', 'KSGT6484', 'HXGU537', 'JIER7373', 'BSJI1111', 'YSUSK73', 'BZJH686', 'BZJZI63K', 'HHZ5272', 'MMF4555', 'FJKL933P', 'WQIL0852', 'SVSN6497', 'VETJD976', 'NPOI4BFN', 'ABAS7262', 'BZFU3636', 'GAGJ3626', 'HSB5Q5QI', 'MAVIC889', 'VGYTF765'];
    let usedCodes = new Set(JSON.parse(localStorage.getItem('usedCodes')) || []); // حفظ الأكواد المستخدمة

    function openCodeModal() {
        document.getElementById('codeModal').style.display = 'flex';
    }

    function openAccountModal() {
        document.getElementById('accountModal').style.display = 'flex';
    }

    function purchase(productName, price) {
        if (balance >= price) {
            selectedProduct = productName;
            selectedPrice = price;
            document.getElementById('productName').textContent = productName;
            document.getElementById('productPrice').textContent = price + ' دينار';
            document.getElementById('purchaseModal').style.display = 'flex';
        } else {
            alert('لا يوجد رصيد كافٍ');
        }
    }

    function confirmPurchase() {
        const userID = document.getElementById('userID').value;
        const username = document.getElementById('username').value;

        if (userID && username) {
            balance -= selectedPrice;
            document.getElementById('balanceAmount').textContent = balance;
            alert('تم الشراء بنجاح');
            closeModal();
        } else {
            alert('يرجى إدخال جميع المعلومات');
        }
    }

    function applyCode() {
        const code = document.getElementById('codeInput').value;
        if (validCodes.includes(code) && !usedCodes.has(code)) {
            balance += 4500;
            document.getElementById('balanceAmount').textContent = balance;
            alert('تم إضافة 4500 دينار إلى رصيدك');
            usedCodes.add(code); // إضافة الكود إلى مجموعة الأكواد المستخدمة
            localStorage.setItem('usedCodes', JSON.stringify([...usedCodes])); // حفظ الأكواد المستخدمة في localStorage
            closeModal();
        } else {
            alert('كود غير صحيح أو تم استخدامه بالفعل');
        }
    }

    function saveUsername() {
        const newUsername = document.getElementById('newUsername').value;
        if (newUsername) {
            localStorage.setItem('username', newUsername);
            alert('تم حفظ اسم المستخدم');
            closeModal();
        } else {
            alert('يرجى إدخال اسم المستخدم');
        }
    }

    function closeModal() {
        document.getElementById('purchaseModal').style.display = 'none';
        document.getElementById('codeModal').style.display = 'none';
        document.getElementById('accountModal').style.display = 'none';
    }

    function refreshPage() {
        window.location.reload();
    }

    // حفظ الرصيد واسم المستخدم عند الخروج
    window.onbeforeunload = function() {
        localStorage.setItem('balance', balance);
        localStorage.setItem('username', localStorage.getItem('username'));
        localStorage.setItem('usedCodes', JSON.stringify([...usedCodes])); // حفظ الأكواد المستخدمة في localStorage
    };

    // استرجاع الرصيد واسم المستخدم عند الدخول
    window.onload = function() {
        balance = parseInt(localStorage.getItem('balance')) || 0;
        document.getElementById('balanceAmount').textContent = balance;
        document.getElementById('newUsername').value = localStorage.getItem('username') || '';
    };
</script>

</body>
</html>
