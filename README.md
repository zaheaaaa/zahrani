<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>اختبار صعب</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
        }
        .container {
            margin-top: 50px;
        }
        .hidden {
            display: none;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            margin-top: 20px;
            cursor: pointer;
        }
        .result {
            font-weight: bold;
            color: green;
        }
    </style>
</head>
<body>
    <div class="container">
        <div id="welcome">
            <h1>مرحبًا بك!</h1>
            <button onclick="showGenderOptions()">Welcome</button>
        </div>

        <div id="gender" class="hidden">
            <h2>اختر جنسك</h2>
            <button onclick="showAgeOptions('رجل')">رجل</button>
            <button onclick="showAgeOptions('فتاة')">فتاة</button>
        </div>

        <div id="age" class="hidden">
            <h2>حدد عمرك</h2>
            <button onclick="startQuiz('+18')">+18</button>
            <button onclick="startQuiz('-18')">-18</button>
        </div>

        <div id="quiz" class="hidden">
            <h2>الإجابة على الأسئلة</h2>
            <p id="question">سؤال 1: ما هو السؤال؟</p>
            <input type="text" id="answer">
            <button onclick="submitAnswer()">إرسال الإجابة</button>
        </div>

        <div id="result" class="hidden">
            <h2>النتيجة النهائية</h2>
            <p class="result" id="score"></p>
        </div>
    </div>

    <script>
        let currentQuestion = 0;
        let correctAnswers = 0;
        const totalQuestions = 10;

        // الأسئلة الصعبة المدمجة
        const questions = [
            "ما هي أصغر وحدة في المادة يمكن أن تشارك في التفاعل الكيميائي؟",
            "ما هو العنصر الذي يعتبر الأكثر انتشارًا في الكون؟",
            "ما هو الكوكب الذي يملك أطول يوم بين الكواكب في النظام الشمسي؟",
            "ما هي درجة الحرارة التي تتوقف عندها الجزيئات عن الحركة؟",
            "ما هو العضو الوحيد في جسم الإنسان الذي يمكن أن يعود للنمو بعد استئصاله جزئيًا؟",
            "ما هو العدد الأولي الذي يأتي بعد 101؟",
            "ما هو الفرق بين الجذر التربيعي لـ 81 والجذر التكعيبي لـ 27؟",
            "من هو القائد العسكري الذي لم يخسر أي معركة طوال مسيرته المهنية؟",
            "في أي عام وقعت الثورة الفرنسية؟",
            "من هو أول إمبراطور في الإمبراطورية الرومانية؟"
        ];

        function showGenderOptions() {
            document.getElementById('welcome').classList.add('hidden');
            document.getElementById('gender').classList.remove('hidden');
        }

        function showAgeOptions(gender) {
            document.getElementById('gender').classList.add('hidden');
            document.getElementById('age').classList.remove('hidden');
        }

        function startQuiz(age) {
            document.getElementById('age').classList.add('hidden');
            document.getElementById('quiz').classList.remove('hidden');
            showQuestion();
        }

        function showQuestion() {
            if (currentQuestion < totalQuestions) {
                document.getElementById('question').textContent = `سؤال ${currentQuestion + 1}: ${questions[currentQuestion]}`;
            } else {
                showResult();
            }
        }

        function submitAnswer() {
            const answer = document.getElementById('answer').value;
            // تحقق من الإجابة (يمكنك تعديل هذا للتحقق الفعلي)
            if (answer === 'الإجابة الصحيحة') {  // يمكنك تعديل الإجابة الصحيحة هنا حسب الأسئلة
                correctAnswers++;
            }
            document.getElementById('answer').value = '';
            currentQuestion++;
            showQuestion();
        }

        function showResult() {
            document.getElementById('quiz').classList.add('hidden');
            document.getElementById('result').classList.remove('hidden');
            document.getElementById('score').textContent = `لقد أجبت بشكل صحيح على ${correctAnswers} من ${totalQuestions} أسئلة.`;
        }
    </script>
</body>
</html>
