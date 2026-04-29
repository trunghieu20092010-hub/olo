<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quick Quiz</title>
    <style>
        body {
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #0d0d0d;
            font-family: 'Inter', 'Segoe UI', sans-serif;
            color: #bc13fe; /* Tông màu tím neon đồng bộ */
            overflow: hidden;
        }

        #quiz-container {
            text-align: center;
            padding: 40px;
            border-radius: 10px;
            background: #141414;
            border: 1px solid #bc13fe;
            box-shadow: 0 0 15px rgba(188, 19, 254, 0.3);
            max-width: 450px;
            width: 85%;
        }

        h2 {
            font-size: 1.4rem;
            margin-bottom: 30px;
            min-height: 60px;
        }

        .btn-group {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }

        button {
            padding: 15px;
            border: 1px solid #bc13fe;
            border-radius: 5px;
            background: transparent;
            color: #bc13fe;
            cursor: pointer;
            transition: all 0.2s ease;
            font-size: 1rem;
        }

        button:hover {
            background: #bc13fe;
            color: #000;
        }

        #result {
            display: none;
        }

        .error-text {
            color: #ff3e3e; /* Màu đỏ cảnh báo nhẹ */
            font-weight: bold;
            font-size: 1.8rem;
            margin-bottom: 15px;
        }

        .final-answer {
            font-size: 2.2rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-top: 10px;
        }

        /* Hiệu ứng mờ dần khi chuyển câu hỏi */
        .fade {
            animation: fadeIn 0.3s;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
    </style>
</head>
<body>

    <div id="quiz-container">
        <div id="question-box" class="fade">
            <h2 id="question-text">Câu 1: Định nghĩa của "Cute" là gì?</h2>
            <div class="btn-group">
                <button onclick="nextQuestion()">Đáng yêu</button>
                <button onclick="nextQuestion()">Dễ thương</button>
                <button onclick="nextQuestion()">Xinh xắn</button>
                <button onclick="nextQuestion()">Khả ái</button>
            </div>
        </div>

        <div id="result" class="fade">
            <div class="error-text">SAI RỒI!</div>
            <p style="color: #fff; font-size: 1.2rem;">Đáp án những câu trên chính là:</p>
            <div class="final-answer">BẠN 🫵</div>
        </div>
    </div>

    <script>
        let currentStep = 1;
        const questions = [
            "Câu 1: Định nghĩa của 'Cute' là gì?",
            "Câu 2: Ai là người dễ thương nhất thế giới?",
            "Câu 3: Từ nào đồng nghĩa với 'Đáng yêu'?",
            "Câu 4: Cuối cùng, 'Cute' có nghĩa là gì?"
        ];

        function nextQuestion() {
            const box = document.getElementById('question-box');
            box.classList.remove('fade');
            void box.offsetWidth; // Trigger reflow
            box.classList.add('fade');

            if (currentStep < questions.length) {
                document.getElementById('question-text').innerText = questions[currentStep];
                currentStep++;
            } else {
                showResult();
            }
        }

        function showResult() {
            document.getElementById('question-box').style.display = 'none';
            document.getElementById('result').style.display = 'block';
        }
    </script>
</body>
</html>
