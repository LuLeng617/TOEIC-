# TOEIC-
TOEIC證照班
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>多益證照班 - 學習助手</title>
    <style>
        :root { --primary: #2c3e50; --accent: #e74c3c; }
        body { font-family: "Microsoft JhengHei", sans-serif; background: #f4f7f6; padding: 20px; color: var(--primary); }
        .container { max-width: 600px; margin: auto; background: white; padding: 30px; border-radius: 12px; box-shadow: 0 4px 6px rgba(0,0,0,0.1); }
        .course-info { background: #ecf0f1; padding: 15px; border-radius: 8px; margin-bottom: 20px; font-size: 0.9em; }
        .quiz-box { border: 2px solid #ddd; padding: 20px; border-radius: 8px; text-align: center; }
        input { width: 80%; padding: 10px; margin: 10px 0; border: 1px solid #ccc; border-radius: 4px; font-size: 1.1em; }
        button { background: var(--primary); color: white; border: none; padding: 10px 20px; border-radius: 4px; cursor: pointer; }
        button:hover { opacity: 0.9; }
        #feedback { font-weight: bold; margin-top: 10px; }
    </style>
</head>
<body>

<div class="container">
    <h2>多益證照班學習助手</h2>
    
    <div class="course-info">
        <strong>🚩 近期目標：</strong>
        <ul id="goal-list">
            <li>Easy Test 聽力需達 110 分以上</li>
            <li>5/25 前後測，5/31 正式考試</li>
        </ul>
    </div>

    <div class="quiz-box">
        <p>請輸入單字的英文：</p>
        <h3 id="ch-word">載入中...</h3>
        <input type="text" id="user-input" placeholder="Type here..." autocomplete="off">
        <br>
        <button onclick="checkAnswer()">驗證答案</button>
        <p id="feedback"></p>
    </div>
</div>

<script>
    // 單字資料庫 (建議之後從後台或 JSON 檔案匯入)
    const wordBank = [
        { en: "requirement", ch: "需求/條件" },
        { en: "procedure", ch: "程序/步驟" },
        { en: "candidate", ch: "候選人/應試者" },
        { en: "submit", ch: "提交" }
    ];

    let currentIdx = 0;

    function nextQuestion() {
        currentIdx = Math.floor(Math.random() * wordBank.length);
        document.getElementById('ch-word').innerText = wordBank[currentIdx].ch;
        document.getElementById('user-input').value = "";
        document.getElementById('feedback').innerText = "";
    }

    function checkAnswer() {
        const userAns = document.getElementById('user-input').value.trim().toLowerCase();
        const correctAns = wordBank[currentIdx].en.toLowerCase();
        const feedback = document.getElementById('feedback');

        if (userAns === correctAns) {
            feedback.innerText = "✅ 正確！";
            feedback.style.color = "green";
            setTimeout(nextQuestion, 1000); // 1秒後自動下一題
        } else {
            feedback.innerText = `❌ 錯誤，答案是 ${wordBank[currentIdx].en}`;
            feedback.style.color = "red";
        }
    }

    // 初始化
    nextQuestion();
</script>

</body>
</html>
