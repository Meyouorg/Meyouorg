<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <title>Factory QC Tool</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
        }
        body {
            background-color: #f5f5f5;
            padding: 20px;
        }
        .container {
            max-width: 600px;
            margin: 0 auto;
            background: white;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        h2 {
            text-align: center;
            margin-bottom: 20px;
            color: #333;
        }
        .box {
            margin: 15px 0;
            padding: 15px;
            border: 1px solid #ddd;
            border-radius: 8px;
        }
        input, button {
            width: 100%;
            padding: 10px;
            margin: 8px 0;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
        }
        button {
            background-color: #4CAF50;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
        .result {
            margin-top: 10px;
            padding: 10px;
            background: #f0f8ff;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>🏭 Factory QC Helper (GitHub Code)</h2>

        <!-- 中英翻译 -->
        <div class="box">
            <h3>1. 中英翻译</h3>
            <input type="text" id="word" placeholder="输入中文/英文：合格 / Pass">
            <button onclick="doTranslate()">翻译</button>
            <div id="transResult" class="result"></div>
        </div>

        <!-- 工资计算 -->
        <div class="box">
            <h3>2. 工资计算</h3>
            <input type="number" id="dayPay" placeholder="日薪">
            <input type="number" id="days" placeholder="上班天数">
            <button onclick="calcSalary()">计算</button>
            <div id="salaryResult" class="result"></div>
        </div>

        <!-- QC检验 -->
        <div class="box">
            <h3>3. QC检验</h3>
            <input type="text" id="batch" placeholder="批次号：A001">
            <input type="text" id="res" placeholder="结果：合格 / 不合格">
            <button onclick="qcCheck()">记录</button>
            <div id="qcResult" class="result"></div>
        </div>
    </div>

    <script>
        // 1. 翻译
        function doTranslate() {
            let word = document.getElementById("word").value.trim();
            let map = {
                "合格":"Pass", "不合格":"Fail",
                "检验":"Inspect", "批次":"Batch",
                "Pass":"合格", "Fail":"不合格"
            };
            let out = map[word] || "未找到";
            document.getElementById("transResult").innerText = "结果：" + out;
        }

        // 2. 算工资
        function calcSalary() {
            let day = Number(document.getElementById("dayPay").value);
            let d = Number(document.getElementById("days").value);
            let total = day * d;
            document.getElementById("salaryResult").innerText = "总工资：" + total;
        }

        // 3. QC检验
        function qcCheck() {
            let b = document.getElementById("batch").value;
            let r = document.getElementById("res").value;
            let text = 批次 ${b}：${r};
            document.getElementById("qcResult").innerText = text;
        }
    </script>
</body>
</html>
