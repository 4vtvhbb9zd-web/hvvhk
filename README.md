# hvvhk
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>اختبار المول - الكيمياء</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            color: #333;
            line-height: 1.6;
            padding: 20px;
            min-height: 100vh;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background-color: rgba(255, 255, 255, 0.95);
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            overflow: hidden;
        }
        
        header {
            background: linear-gradient(90deg, #2c3e50, #4a6491);
            color: white;
            padding: 25px;
            text-align: center;
            border-bottom: 5px solid #3498db;
        }
        
        h1 {
            font-size: 2.2rem;
            margin-bottom: 10px;
        }
        
        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
        }
        
        .content {
            display: flex;
            flex-wrap: wrap;
        }
        
        .video-section {
            flex: 1;
            min-width: 300px;
            padding: 20px;
            background-color: #f8f9fa;
            border-left: 1px solid #e0e0e0;
        }
        
        .quiz-section {
            flex: 2;
            min-width: 300px;
            padding: 20px;
        }
        
        .video-container {
            background: #2c3e50;
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 20px;
            color: white;
            text-align: center;
        }
        
        .video-wrapper {
            position: relative;
            padding-bottom: 56.25%; /* 16:9 aspect ratio */
            height: 0;
            overflow: hidden;
            border-radius: 8px;
            margin: 15px 0;
        }
        
        .video-wrapper iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: none;
        }
        
        .lesson-content {
            background: white;
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
            margin-top: 15px;
        }
        
        .question {
            background: white;
            padding: 20px;
            margin-bottom: 20px;
            border-radius: 10px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
            display: none;
        }
        
        .question.active {
            display: block;
        }
        
        .question-number {
            font-weight: bold;
            color: #2c3e50;
            margin-bottom: 10px;
            font-size: 1.1rem;
        }
        
        .question-text {
            font-size: 1.1rem;
            margin-bottom: 20px;
            color: #2c3e50;
        }
        
        .options {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        
        .option {
            padding: 12px 15px;
            background: #f8f9fa;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .option:hover {
            background: #e9ecef;
            border-color: #3498db;
        }
        
        .option.correct {
            background: #d4edda;
            border-color: #28a745;
            color: #155724;
        }
        
        .option.incorrect {
            background: #f8d7da;
            border-color: #dc3545;
            color: #721c24;
        }
        
        .explanation {
            margin-top: 15px;
            padding: 15px;
            border-radius: 8px;
            display: none;
        }
        
        .explanation.correct {
            background: #d4edda;
            border-left: 5px solid #28a745;
            display: block;
        }
        
        .explanation.incorrect {
            background: #f8d7da;
            border-left: 5px solid #dc3545;
            display: block;
        }
        
        .navigation {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
        }
        
        button {
            padding: 12px 25px;
            background: #3498db;
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            transition: background 0.3s;
        }
        
        button:hover {
            background: #2980b9;
        }
        
        button:disabled {
            background: #bdc3c7;
            cursor: not-allowed;
        }
        
        .results {
            text-align: center;
            padding: 30px;
            display: none;
        }
        
        .results.active {
            display: block;
        }
        
        .score {
            font-size: 2.5rem;
            font-weight: bold;
            color: #2c3e50;
            margin: 20px 0;
        }
        
        .percentage {
            font-size: 1.5rem;
            color: #3498db;
            margin-bottom: 20px;
        }
        
        .progress-bar {
            height: 10px;
            background: #e0e0e0;
            border-radius: 5px;
            margin: 20px 0;
            overflow: hidden;
        }
        
        .progress {
            height: 100%;
            background: #3498db;
            width: 0%;
            transition: width 0.5s;
        }
        
        .summary {
            margin-top: 20px;
            text-align: right;
        }
        
        .retry-btn {
            background: #2ecc71;
            margin-top: 20px;
        }
        
        .retry-btn:hover {
            background: #27ae60;
        }
        
        .student-grade {
            margin: 25px 0;
            padding: 20px;
            background: linear-gradient(135deg, #f8f9fa, #e9ecef);
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        
        .grade-circle {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            background: #3498db;
            margin: 0 auto;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 2.5rem;
            font-weight: bold;
            box-shadow: 0 5px 15px rgba(52, 152, 219, 0.4);
        }
        
        .grade-text {
            margin-top: 15px;
            font-size: 1.3rem;
            color: #2c3e50;
            font-weight: bold;
        }
        
        .student-info {
            background: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            margin-bottom: 20px;
            text-align: center;
        }
        
        .student-info h2 {
            color: #2c3e50;
            margin-bottom: 20px;
        }
        
        .form-group {
            margin-bottom: 20px;
            text-align: right;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: #2c3e50;
        }
        
        .form-group input {
            width: 100%;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 1rem;
            transition: border-color 0.3s;
        }
        
        .form-group input:focus {
            border-color: #3498db;
            outline: none;
        }
        
        .start-btn {
            background: #2ecc71;
            font-size: 1.2rem;
            padding: 15px 40px;
        }
        
        .start-btn:hover {
            background: #27ae60;
        }
        
        .student-details {
            background: #f8f9fa;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
            text-align: center;
            border-right: 5px solid #3498db;
        }
        
        .student-details h3 {
            color: #2c3e50;
            margin-bottom: 10px;
        }
        
        .final-percentage {
            font-size: 3rem;
            font-weight: bold;
            color: #2c3e50;
            margin: 20px 0;
            text-align: center;
        }
        
        .final-grade {
            font-size: 2rem;
            color: #3498db;
            margin-bottom: 20px;
            text-align: center;
        }
        
        @media (max-width: 768px) {
            .content {
                flex-direction: column;
            }
            
            .video-section {
                border-left: none;
                border-bottom: 1px solid #e0e0e0;
            }
            
            .grade-circle {
                width: 120px;
                height: 120px;
                font-size: 2rem;
            }
            
            .final-percentage {
                font-size: 2.5rem;
            }
            
            .final-grade {
                font-size: 1.5rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>اختبار الكيمياء - درس المول</h1>
            <p class="subtitle">اختبر معرفتك في مفهوم المول والكتلة المولية وعدد أفوجادرو</p>
        </header>
        
        <div class="content">
            <div class="quiz-section">
                <!-- قسم إدخال بيانات الطالب -->
                <div id="student-form" class="student-info">
                    <h2>بيانات الطالب</h2>
                    <div class="form-group">
                        <label for="student-name">اسم الطالب:</label>
                        <input type="text" id="student-name" placeholder="أدخل اسمك الكامل">
                    </div>
                    <div class="form-group">
                        <label for="student-class">رقم الشعبة:</label>
                        <input type="text" id="student-class" placeholder="أدخل رقم الشعبة">
                    </div>
                    <button id="start-btn" class="start-btn">بدء الاختبار</button>
                </div>
                
                <!-- قسم عرض بيانات الطالب -->
                <div id="student-display" class="student-details" style="display: none;">
                    <h3 id="display-name"></h3>
                    <p id="display-class"></p>
                </div>
                
                <!-- قسم الأسئلة -->
                <div id="question-container">
                    <!-- الأسئلة سيتم إضافتها هنا ديناميكيًا -->
                </div>
                
                <div class="navigation">
                    <button id="prev-btn" disabled>السؤال السابق</button>
                    <button id="next-btn" disabled>السؤال التالي</button>
                </div>
                
                <!-- قسم النتائج -->
                <div id="results" class="results">
                    <h2>نتيجة الاختبار</h2>
                    
                    <div class="student-details">
                        <h3 id="result-name"></h3>
                        <p id="result-class"></p>
                    </div>
                    
                    <div class="final-percentage" id="final-percentage">0%</div>
                    <div class="final-grade" id="final-grade">ضعيف</div>
                    
                    <div class="student-grade">
                        <div class="grade-circle" id="grade-circle">0%</div>
                        <div class="grade-text" id="grade-text">ضعيف</div>
                    </div>
                    
                    <div class="score">لقد أجبت على <span id="correct-answers">0</span> من أصل 50 سؤالاً بشكل صحيح</div>
                    <div class="percentage">النسبة المئوية: <span id="percentage">0%</span></div>
                    
                    <div class="progress-bar">
                        <div class="progress" id="progress-bar"></div>
                    </div>
                    
                    <div class="summary" id="summary">
                        <!-- الملخص سيتم إضافته هنا -->
                    </div>
                    
                    <button class="retry-btn" id="retry-btn">إعادة الاختبار</button>
                </div>
            </div>
            
            <div class="video-section">
                <div class="video-container">
                    <h3>شرح درس المول</h3>
                    <div class="video-wrapper">
                        <iframe src="https://www.youtube.com/embed/8s45w1twUkE" 
                                title="شرح درس المول" 
                                frameborder="0" 
                                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
                                allowfullscreen>
                        </iframe>
                    </div>
                    <p>شاهد هذا الفيديو لمراجعة مفهوم المول قبل البدء بالاختبار</p>
                </div>
                
                <div class="lesson-content">
                    <h3>معلومات سريعة عن المول</h3>
                    <ul style="padding-right: 20px; margin-top: 10px;">
                        <li>المول هو وحدة قياس كمية المادة</li>
                        <li>عدد أفوجادرو = \( 6.02 \times 10^{23} \)</li>
                        <li>الكتلة المولية = كتلة مول واحد من المادة</li>
                        <li>لتحويل المولات إلى جسيمات: عدد الجسيمات = عدد المولات × عدد أفوجادرو</li>
                        <li>لتحويل الكتلة إلى مولات: عدد المولات = الكتلة ÷ الكتلة المولية</li>
                    </ul>
                </div>
            </div>
        </div>
    </div>

    <script>
        // بيانات الأسئلة (50 سؤالاً)
        const questions = [
            {
                question: "ما قيمة عدد أفوجادرو؟",
                options: ["6.02 × 10²²", "6.02 × 10²³", "6.02 × 10²⁴"],
                correct: 1,
                explanation: "عدد أفوجادرو يساوي 6.02 × 10²³ وهو عدد الجسيمات في المول الواحد من أي مادة."
            },
            {
                question: "المول هو وحدة قياس:",
                options: ["الكتلة", "الحجم", "كمية المادة"],
                correct: 2,
                explanation: "المول هو الوحدة الأساسية في النظام الدولي للوحدات لقياس كمية المادة."
            },
            {
                question: "عدد الجسيمات في 1 مول من أي مادة يساوي:",
                options: ["6.02 × 10²²", "6.02 × 10²³", "6.02 × 10²⁴"],
                correct: 1,
                explanation: "يحتوي المول الواحد من أي مادة على عدد أفوجادرو من الجسيمات وهو 6.02 × 10²³."
            },
            {
                question: "المول الواحد من الحديد يحتوي على:",
                options: ["6.02 × 10²٢ ذرة حديد", "6.02 × 10²³ ذرة حديد", "6.02 × 10²⁴ ذرة حديد"],
                correct: 1,
                explanation: "المول الواحد من أي عنصر يحتوي على عدد أفوجادرو من الذرات."
            },
            {
                question: "ما نوع الجسيمات في 1 مول من غاز النيتروجين N₂؟",
                options: ["ذرات", "جزيئات", "أيونات"],
                correct: 1,
                explanation: "غاز النيتروجين N₂ يتكون من جزيئات ثنائية الذرة، لذا المول الواحد يحتوي على عدد أفوجادرو من الجزيئات."
            },
            {
                question: "كم عدد الجزيئات في 2 مول من الماء؟",
                options: ["3.01 × 10²³ جزيء", "6.02 × 10²³ جزيء", "1.204 × 10²⁴ جزيء"],
                correct: 2,
                explanation: "عدد الجزيئات = عدد المولات × عدد أفوجادرو = 2 × 6.02 × 10²³ = 1.204 × 10²⁴ جزيء."
            },
            {
                question: "كم عدد الذرات في 0.5 مول من الحديد؟",
                options: ["3.01 × 10²³ ذرة", "6.02 × 10²³ ذرة", "1.204 × 10²⁴ ذرة"],
                correct: 0,
                explanation: "عدد الذرات = عدد المولات × عدد أفوجادرو = 0.5 × 6.02 × 10²³ = 3.01 × 10²³ ذرة."
            },
            {
                question: "تحويل 3.01 × 10²³ ذرة إلى مولات:",
                options: ["0.25 مول", "0.5 مول", "1 مول"],
                correct: 1,
                explanation: "عدد المولات = عدد الجسيمات ÷ عدد أفوجادرو = 3.01 × 10²³ ÷ 6.02 × 10²³ = 0.5 مول."
            },
            {
                question: "عدد المولات في 1.204 × 10²⁴ جزيء:",
                options: ["1 مول", "2 مول", "3 مول"],
                correct: 1,
                explanation: "عدد المولات = عدد الجسيمات ÷ عدد أفوجادرو = 1.204 × 10²⁴ ÷ 6.02 × 10²³ = 2 مول."
            },
            {
                question: "كم جزيء في 0.25 مول من NaCl؟",
                options: ["1.505 × 10²³ جزيء", "3.01 × 10²³ جزيء", "6.02 × 10²³ جزيء"],
                correct: 0,
                explanation: "عدد الجزيئات = عدد المولات × عدد أفوجادرو = 0.25 × 6.02 × 10²³ = 1.505 × 10²³ جزيء."
            },
            {
                question: "ما الكتلة المولية لـ CO₂؟ (C=12, O=16)",
                options: ["28 g/mol", "32 g/mol", "44 g/mol"],
                correct: 2,
                explanation: "الكتلة المولية لـ CO₂ = 12 + (16×2) = 44 g/mol."
            },
            {
                question: "ما الكتلة المولية لـ H₂O؟ (H=1, O=16)",
                options: ["16 g/mol", "18 g/mol", "20 g/mol"],
                correct: 1,
                explanation: "الكتلة المولية لـ H₂O = (1×2) + 16 = 18 g/mol."
            },
            {
                question: "ما الكتلة المولية لـ NaCl؟ (Na=23, Cl=35.5)",
                options: ["58.5 g/mol", "48.5 g/mol", "68.5 g/mol"],
                correct: 0,
                explanation: "الكتلة المولية لـ NaCl = 23 + 35.5 = 58.5 g/mol."
            },
            {
                question: "ما الكتلة المولية لـ H₂SO₄؟ (H=1, S=32, O=16)",
                options: ["96 g/mol", "98 g/mol", "100 g/mol"],
                correct: 1,
                explanation: "الكتلة المولية لـ H₂SO₄ = (1×2) + 32 + (16×4) = 98 g/mol."
            },
            {
                question: "ما الكتلة المولية لـ CaCO₃？ (Ca=40, C=12, O=16)",
                options: ["96 g/mol", "100 g/mol", "116 g/mol"],
                correct: 1,
                explanation: "الكتلة المولية لـ CaCO₃ = 40 + 12 + (16×3) = 100 g/mol."
            },
            {
                question: "كم كتلة 2 مول من CO₂？",
                options: ["44 g", "88 g", "132 g"],
                correct: 1,
                explanation: "الكتلة = عدد المولات × الكتلة المولية = 2 × 44 = 88 g."
            },
            {
                question: "كم كتلة 0.5 مول من H₂O？",
                options: ["9 g", "18 g", "36 g"],
                correct: 0,
                explanation: "الكتلة = عدد المولات × الكتلة المولية = 0.5 × 18 = 9 g."
            },
            {
                question: "كم عدد المولات في 36 g من H₂O？",
                options: ["1 مول", "2 مول", "3 مول"],
                correct: 1,
                explanation: "عدد المولات = الكتلة ÷ الكتلة المولية = 36 ÷ 18 = 2 مول."
            },
            {
                question: "كم عدد المولات في 117 g من NaCl？",
                options: ["1 مول", "2 مول", "3 مول"],
                correct: 1,
                explanation: "عدد المولات = الكتلة ÷ الكتلة المولية = 117 ÷ 58.5 = 2 مول."
            },
            {
                question: "كم كتلة 3 مول من CaCO₃？",
                options: ["200 g", "300 g", "400 g"],
                correct: 1,
                explanation: "الكتلة = عدد المولات × الكتلة المولية = 3 × 100 = 300 g."
            },
            {
                question: "كم عدد الجزيئات في 18 g من H₂O？",
                options: ["3.01 × 10²³ جزيء", "6.02 × 10²³ جزيء", "1.204 × 10²⁴ جزيء"],
                correct: 1,
                explanation: "عدد المولات = 18 ÷ 18 = 1 مول، عدد الجزيئات = 1 × 6.02 × 10²³ = 6.02 × 10²³ جزيء."
            },
            {
                question: "كم عدد الذرات في 56 g من الحديد？",
                options: ["3.01 × 10²³ ذرة", "6.02 × 10²³ ذرة", "1.204 × 10²⁴ ذرة"],
                correct: 1,
                explanation: "عدد المولات = 56 ÷ 56 = 1 مول، عدد الذرات = 1 × 6.02 × 10²³ = 6.02 × 10²³ ذرة."
            },
            {
                question: "كم كتلة 3.01 × 10²³ جزيء من CO₂？",
                options: ["11 g", "22 g", "44 g"],
                correct: 1,
                explanation: "عدد المولات = 3.01 × 10²³ ÷ 6.02 × 10²³ = 0.5 مول، الكتلة = 0.5 × 44 = 22 g."
            },
            {
                question: "كم كتلة 1.204 × 10²⁴ ذرة من الحديد？",
                options: ["56 g", "112 g", "168 g"],
                correct: 1,
                explanation: "عدد المولات = 1.204 × 10²⁴ ÷ 6.02 × 10²³ = 2 مول، الكتلة = 2 × 56 = 112 g."
            },
            {
                question: "كم عدد الجزيئات في 44 g من CO₂？",
                options: ["3.01 × 10²³ جزيء", "6.02 × 10²³ جزيء", "1.204 × 10²⁴ جزيء"],
                correct: 1,
                explanation: "عدد المولات = 44 ÷ 44 = 1 مول، عدد الجزيئات = 1 × 6.02 × 10²³ = 6.02 × 10²³ جزيء."
            },
            {
                question: "إذا كان لدينا 0.5 مول من الذهب، فما عدد الذرات？",
                options: ["3.01 × 10²³ ذرة", "6.02 × 10²³ ذرة", "1.204 × 10²⁴ ذرة"],
                correct: 0,
                explanation: "عدد الذرات = عدد المولات × عدد أفوجادرو = 0.5 × 6.02 × 10²³ = 3.01 × 10²³ ذرة."
            },
            {
                question: "كم كتلة 2.5 مول من ملح الطعام NaCl？",
                options: ["116.25 g", "146.25 g", "176.25 g"],
                correct: 1,
                explanation: "الكتلة = عدد المولات × الكتلة المولية = 2.5 × 58.5 = 146.25 g."
            },
            {
                question: "كم عدد المولات في 196 g من H₂SO₄？",
                options: ["1 مول", "2 مول", "3 مول"],
                correct: 1,
                explanation: "عدد المولات = الكتلة ÷ الكتلة المولية = 196 ÷ 98 = 2 مول."
            },
            {
                question: "كم جزيء في 9 g من الماء？",
                options: ["3.01 × 10²³ جزيء", "6.02 × 10²³ جزيء", "1.204 × 10²⁴ جزيء"],
                correct: 0,
                explanation: "عدد المولات = 9 ÷ 18 = 0.5 مول، عدد الجزيئات = 0.5 × 6.02 × 10²³ = 3.01 × 10²³ جزيء."
            },
            {
                question: "تحويل 84 g من NaHCO₃ إلى مولات (الكتلة المولية = 84 g/mol):",
                options: ["0.5 مول", "1 مول", "2 مول"],
                correct: 1,
                explanation: "عدد المولات = الكتلة ÷ الكتلة المولية = 84 ÷ 84 = 1 مول."
            },
            {
                question: "كم عدد ذرات الهيدروجين في 1 مول من CH₄？",
                options: ["6.02 × 10²³ ذرة", "1.204 × 10²⁴ ذرة", "2.408 × 10²⁴ ذرة"],
                correct: 2,
                explanation: "جزيء CH₄ يحتوي على 4 ذرات هيدروجين، لذا عدد ذرات الهيدروجين = 4 × 6.02 × 10²³ = 2.408 × 10²⁴ ذرة."
            },
            {
                question: "كم عدد ذرات الأكسجين في 0.5 مول من CO₂？",
                options: ["3.01 × 10²³ ذرة", "6.02 × 10²³ ذرة", "1.204 × 10²⁴ ذرة"],
                correct: 1,
                explanation: "جزيء CO₂ يحتوي على 2 ذرة أكسجين، لذا عدد ذرات الأكسجين = 0.5 × 2 × 6.02 × 10²³ = 6.02 × 10²³ ذرة."
            },
            {
                question: "ما كتلة 0.1 مول من هيدروكسيد الصوديوم NaOH？ (Na=23, O=16, H=1)",
                options: ["2 g", "4 g", "6 g"],
                correct: 1,
                explanation: "الكتلة المولية لـ NaOH = 23 + 16 + 1 = 40 g/mol، الكتلة = 0.1 × 40 = 4 g."
            },
            {
                question: "كم عدد المولات في 180 g من الجلوكوز C₆H₁₂O₆？ (الكتلة المولية = 180 g/mol)",
                options: ["0.5 مول", "1 مول", "2 مول"],
                correct: 1,
                explanation: "عدد المولات = الكتلة ÷ الكتلة المولية = 180 ÷ 180 = 1 مول."
            },
            {
                question: "كم جزيء في 71 g من غاز الكلور Cl₂？",
                options: ["3.01 × 10²³ جزيء", "6.02 × 10²³ جزيء", "1.204 × 10²⁴ جزيء"],
                correct: 1,
                explanation: "الكتلة المولية لـ Cl₂ = 35.5 × 2 = 71 g/mol، عدد المولات = 71 ÷ 71 = 1 مول، عدد الجزيئات = 1 × 6.02 × 10²³ = 6.02 × 10²³ جزيء."
            },
            {
                question: "المول الواحد من أي غاز في الظروف القياسية يحتل حجم:",
                options: ["22.4 لتر", "24.5 لتر", "25.4 لتر"],
                correct: 0,
                explanation: "المول الواحد من أي غاز في الظروف القياسية (STP) يحتل حجم 22.4 لتر."
            },
            {
                question: "كم عدد أيونات الكلور في 0.5 مول من CaCl₂？",
                options: ["3.01 × 10²³ أيون", "6.02 × 10²³ أيون", "1.204 × 10²⁴ أيون"],
                correct: 1,
                explanation: "جزيء CaCl₂ يحتوي على 2 أيون كلور، لذا عدد أيونات الكلور = 0.5 × 2 × 6.02 × 10²³ = 6.02 × 10²³ أيون."
            },
            {
                question: "ما كتلة 0.25 مول من كبريتات النحاس CuSO₄？ (Cu=64, S=32, O=16)",
                options: ["30 g", "40 g", "50 g"],
                correct: 1,
                explanation: "الكتلة المولية لـ CuSO₄ = 64 + 32 + (16×4) = 160 g/mol، الكتلة = 0.25 × 160 = 40 g."
            },
            {
                question: "كم عدد المولات في 120 g من هيدروكسيد المغنيسيوم Mg(OH)₂？ (Mg=24, O=16, H=1)",
                options: ["1 مول", "2 مول", "3 مول"],
                correct: 1,
                explanation: "الكتلة المولية لـ Mg(OH)₂ = 24 + (16×2) + (1×2) = 58 g/mol، عدد المولات = 120 ÷ 58 ≈ 2 مول."
            },
            {
                question: "إذا كان لدينا 0.2 مول من حمض HCl، فما عدد الجزيئات？",
                options: ["1.204 × 10²³ جزيء", "3.01 × 10²³ جزيء", "6.02 × 10²³ جزيء"],
                correct: 0,
                explanation: "عدد الجزيئات = عدد المولات × عدد أفوجادرو = 0.2 × 6.02 × 10²³ = 1.204 × 10²³ جزيء."
            },
            {
                question: "ما الكتلة المولية لمركب كلوريد الصوديوم NaCl？",
                options: ["23.5 g/mol", "35.5 g/mol", "58.5 g/mol"],
                correct: 2,
                explanation: "الكتلة المولية لـ NaCl = 23 + 35.5 = 58.5 g/mol."
            },
            {
                question: "كم عدد المولات في عينة كتلتها 31.1 g من الذهب Au (الكتلة المولية = 197 g/mol)？",
                options: ["0.158 mol", "0.264 mol", "0.532 mol"],
                correct: 0,
                explanation: "عدد المولات = الكتلة ÷ الكتلة المولية = 31.1 ÷ 197 ≈ 0.158 مول."
            },
            {
                question: "ما عدد ذرات الصوديوم في 0.15 mol من Na？",
                options: ["9.03×10²² ذرة", "6.02×10²³ ذرة", "1.204×10²⁴ ذرة"],
                correct: 0,
                explanation: "عدد الذرات = عدد المولات × عدد أفوجادرو = 0.15 × 6.02 × 10²³ = 9.03 × 10²² ذرة."
            },
            {
                question: "احسب الكتلة بالجرام لـ 0.1 mol من Al (الكتلة المولية = 27 g/mol):",
                options: ["2.7 g", "5.4 g", "10.8 g"],
                correct: 0,
                explanation: "الكتلة = عدد المولات × الكتلة المولية = 0.1 × 27 = 2.7 g."
            },
            {
                question: "احسب الكتلة المولية لحمض الخليك CH₃COOH:",
                options: ["58 g/mol", "59 g/mol", "60 g/mol"],
                correct: 2,
                explanation: "الكتلة المولية لـ CH₃COOH = (12×2) + (1×4) + (16×2) = 60 g/mol."
            },
            {
                question: "أي من الآتي يمثل وحدة قياس الكتلة المولية？",
                options: ["mol", "g/mol", "g"],
                correct: 1,
                explanation: "الكتلة المولية تقاس بوحدة g/mol (جرام لكل مول)."
            },
            {
                question: "ما عدد المولات في 60 g من NaOH (الكتلة المولية = 40 g/mol)？",
                options: ["1 mol", "1.5 mol", "2 mol"],
                correct: 1,
                explanation: "عدد المولات = الكتلة ÷ الكتلة المولية = 60 ÷ 40 = 1.5 مول."
            },
            {
                question: "عند مقارنة عدد ذرات 1 mol من النحاس و1 mol من الكبريت نجد أن:",
                options: ["عدد ذرات النحاس أكبر", "عدد الذرات متساوي", "عدد ذرات الكبريت أكبر"],
                correct: 1,
                explanation: "المول الواحد من أي مادة يحتوي على نفس العدد من الجسيمات (عدد أفوجادرو)."
            },
            {
                question: "كم عدد مولات الأكسجين في 4 mol من Fe₂O₃？",
                options: ["6 mol", "8 mol", "12 mol"],
                correct: 2,
                explanation: "جزيء Fe₂O₃ يحتوي على 3 ذرات أكسجين، لذا عدد مولات الأكسجين = 4 × 3 = 12 مول."
            },
            {
                question: "كم عدد جزيئات الماء الموجودة في 5 mol من H₂O？",
                options: ["2×10²³", "3×10²⁴", "3.01×10²⁴"],
                correct: 2,
                explanation: "عدد الجزيئات = عدد المولات × عدد أفوجادرو = 5 × 6.02 × 10²³ = 3.01 × 10²⁴ جزيء."
            }
        ];

        // تهيئة المتغيرات
        let currentQuestion = 0;
        let userAnswers = new Array(questions.length).fill(null);
        let score = 0;
        let studentName = "";
        let studentClass = "";

        // عناصر DOM
        const studentForm = document.getElementById('student-form');
        const studentDisplay = document.getElementById('student-display');
        const displayName = document.getElementById('display-name');
        const displayClass = document.getElementById('display-class');
        const questionContainer = document.getElementById('question-container');
        const prevBtn = document.getElementById('prev-btn');
        const nextBtn = document.getElementById('next-btn');
        const resultsContainer = document.getElementById('results');
        const resultName = document.getElementById('result-name');
        const resultClass = document.getElementById('result-class');
        const correctAnswersSpan = document.getElementById('correct-answers');
        const percentageSpan = document.getElementById('percentage');
        const finalPercentage = document.getElementById('final-percentage');
        const finalGrade = document.getElementById('final-grade');
        const progressBar = document.getElementById('progress-bar');
        const summaryDiv = document.getElementById('summary');
        const retryBtn = document.getElementById('retry-btn');
        const gradeCircle = document.getElementById('grade-circle');
        const gradeText = document.getElementById('grade-text');
        const startBtn = document.getElementById('start-btn');
        const studentNameInput = document.getElementById('student-name');
        const studentClassInput = document.getElementById('student-class');

        // بدء الاختبار بعد إدخال البيانات
        startBtn.addEventListener('click', function() {
            if (studentNameInput.value.trim() === "" || studentClassInput.value.trim() === "") {
                alert("يرجى إدخال اسم الطالب ورقم الشعبة");
                return;
            }
            
            studentName = studentNameInput.value.trim();
            studentClass = studentClassInput.value.trim();
            
            studentForm.style.display = 'none';
            studentDisplay.style.display = 'block';
            displayName.textContent = `الطالب: ${studentName}`;
            displayClass.textContent = `الشعبة: ${studentClass}`;
            
            initQuiz();
        });

        // تهيئة الاختبار
        function initQuiz() {
            showQuestion(currentQuestion);
            updateNavigation();
        }

        // عرض السؤال الحالي
        function showQuestion(index) {
            questionContainer.innerHTML = '';
            
            const question = questions[index];
            const questionElement = document.createElement('div');
            questionElement.className = 'question active';
            
            let optionsHTML = '';
            question.options.forEach((option, i) => {
                const isSelected = userAnswers[index] === i;
                const isCorrect = userAnswers[index] !== null && i === question.correct;
                const isIncorrect = userAnswers[index] !== null && userAnswers[index] === i && userAnswers[index] !== question.correct;
                
                let optionClass = 'option';
                if (isCorrect) optionClass += ' correct';
                if (isIncorrect) optionClass += ' incorrect';
                
                optionsHTML += `
                    <div class="${optionClass}" onclick="selectOption(${i})">
                        ${option}
                    </div>
                `;
            });
            
            questionElement.innerHTML = `
                <div class="question-number">السؤال ${index + 1} من ${questions.length}</div>
                <div class="question-text">${question.question}</div>
                <div class="options">${optionsHTML}</div>
                ${userAnswers[index] !== null ? `
                    <div class="explanation ${userAnswers[index] === question.correct ? 'correct' : 'incorrect'}">
                        ${question.explanation}
                    </div>
                ` : ''}
            `;
            
            questionContainer.appendChild(questionElement);
        }

        // تحديد خيار
        function selectOption(optionIndex) {
            if (userAnswers[currentQuestion] !== null) return;
            
            userAnswers[currentQuestion] = optionIndex;
            showQuestion(currentQuestion);
            updateNavigation();
        }

        // تحديث أزرار التنقل
        function updateNavigation() {
            // تعطيل زر السابق تماماً (لا يمكن الرجوع للخلف)
            prevBtn.disabled = true;
            
            // تمكين زر التالي فقط إذا تم الإجابة على السؤال الحالي
            nextBtn.disabled = userAnswers[currentQuestion] === null;
            
            if (currentQuestion === questions.length - 1) {
                nextBtn.textContent = 'عرض النتائج';
            } else {
                nextBtn.textContent = 'السؤال التالي';
            }
        }

        // الانتقال إلى السؤال التالي
        function nextQuestion() {
            if (currentQuestion < questions.length - 1) {
                currentQuestion++;
                showQuestion(currentQuestion);
                updateNavigation();
            } else {
                showResults();
            }
        }

        // الانتقال إلى السؤال السابق (معطل)
        function prevQuestion() {
            // لا يمكن الرجوع للخلف
            return;
        }

        // حساب النتيجة وتحديد التقدير
        function calculateScore() {
            score = 0;
            for (let i = 0; i < questions.length; i++) {
                if (userAnswers[i] === questions[i].correct) {
                    score++;
                }
            }
            
            const percentage = Math.round((score / questions.length) * 100);
            
            correctAnswersSpan.textContent = score;
            percentageSpan.textContent = `${percentage}%`;
            finalPercentage.textContent = `${percentage}%`;
            progressBar.style.width = `${percentage}%`;
            gradeCircle.textContent = `${percentage}%`;
            
            // تحديد التقدير بناءً على النسبة
            let grade, color;
            if (percentage >= 90) {
                grade = "ممتاز";
                color = "#27ae60";
            } else if (percentage >= 80) {
                grade = "جيد جداً";
                color = "#2ecc71";
            } else if (percentage >= 70) {
                grade = "جيد";
                color = "#f1c40f";
            } else if (percentage >= 60) {
                grade = "مقبول";
                color = "#e67e22";
            } else {
                grade = "ضعيف";
                color = "#e74c3c";
            }
            
            gradeText.textContent = grade;
            finalGrade.textContent = grade;
            gradeCircle.style.background = color;
            
            // إضافة ملخص
            let summaryHTML = '<h3>ملخص الأداء:</h3><ul>';
            
            if (percentage >= 90) {
                summaryHTML += '<li>أداء ممتاز! لديك فهم قوي لمفهوم المول.</li>';
            } else if (percentage >= 70) {
                summaryHTML += '<li>أداء جيد، لكن يمكنك تحسين فهمك بمراجعة بعض النقاط.</li>';
            } else if (percentage >= 50) {
                summaryHTML += '<li>أداء مقبول، ننصحك بمراجعة درس المول مرة أخرى.</li>';
            } else {
                summaryHTML += '<li>تحتاج إلى مراجعة شاملة لدرس المول.</li>';
            }
            
            summaryHTML += `<li>عدد الإجابات الصحيحة: ${score}</li>`;
            summaryHTML += `<li>عدد الإجابات الخاطئة: ${questions.length - score}</li>`;
            summaryHTML += `<li>نسبة النجاح: ${percentage}%</li>`;
            summaryHTML += `<li>التقدير: ${grade}</li>`;
            summaryHTML += '</ul>';
            
            summaryDiv.innerHTML = summaryHTML;
            
            // عرض بيانات الطالب في النتائج
            resultName.textContent = `الطالب: ${studentName}`;
            resultClass.textContent = `الشعبة: ${studentClass}`;
        }

        // عرض النتائج
        function showResults() {
            calculateScore();
            document.querySelector('.quiz-section').style.display = 'none';
            resultsContainer.classList.add('active');
        }

        // إعادة الاختبار
        function retryQuiz() {
            currentQuestion = 0;
            userAnswers = new Array(questions.length).fill(null);
            score = 0;
            
            document.querySelector('.quiz-section').style.display = 'block';
            resultsContainer.classList.remove('active');
            studentForm.style.display = 'block';
            studentDisplay.style.display = 'none';
            
            // إعادة تعيين حقول الإدخال
            studentNameInput.value = "";
            studentClassInput.value = "";
        }

        // إضافة المستمعين للأحداث
        prevBtn.addEventListener('click', prevQuestion);
        nextBtn.addEventListener('click', nextQuestion);
        retryBtn.addEventListener('click', retryQuiz);

        // جعل الدوال متاحة عالمياً
        window.selectOption = selectOption;
    </script>
</body>
</html>
