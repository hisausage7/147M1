<吃飽太閒做的網站，能幫到你我覺得很開心>
<html lang="zh-Hant">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>147測驗｜單一檔案版</title>
    <style>
            /* 回首頁浮動按鈕 */
            #homeBtn {
        position: absolute;
        top: 100px;               /* 深色模式在20px，這裡放在它下方 */
        right: 20px;
        padding: 10px 20px;
        background: #28a745;
        color: #fff;
        border: none;
        border-radius: 8px;
        text-decoration: none;
        font-size: 1em;
        box-shadow: 0 4px 12px rgba(0,0,0,.15);
        transition: background .3s, transform .2s, box-shadow .2s;
        z-index: 1000;
      }
      #homeBtn:hover {
        background: #218838;
        transform: translateY(-2px);
        box-shadow: 0 6px 16px rgba(0,0,0,.25);
      }
      body.dark #homeBtn {
        background: #2e7d32;
      }
      body.dark #homeBtn:hover {
        background: #25652a;
      }

            body {
              font-family: Arial, sans-serif;
              margin: 0;
              padding: 40px;
              font-size: 1.6em;
              background: #f0f4f8;
              color: #000;
              transition: background-color 0.5s, color 0.5s;
            }
            body.dark { background: #121212; color: #fff; }
            #container {
              max-width: 1200px; margin: auto; background: #fff; padding: 40px;
              border-radius: 20px; box-shadow: 0 0 10px rgba(0,0,0,.1);
              transition: background-color .5s, color .5s;
            }
            body.dark #container { background: #1e1e1e; }
            .hidden { display: none; }
            h1, h2 { text-align: center; font-size: 2.4em; }
            #rules {
              background: #e9ecef; padding: 20px; margin-bottom: 40px;
              border-radius: 10px; font-size: 1.2em;
            }
            body.dark #rules { background: #333; }
            .btn {
              background: #007bff; color: #fff; border: none; padding: 20px 40px;
              margin: 10px; border-radius: 10px; cursor: pointer; font-size: 1.2em;
              transition: background-color .3s;
            }
            .btn:hover { background: #0056b3; }
            #leaveBtn { background: #dc3545; }
            #progress, #timer { font-weight: bold; font-size: 1.4em; }
            .progress-container {
              background: #ddd; height: 10px; border-radius: 5px; margin-top: 20px; overflow: hidden;
            }
            body.dark .progress-container { background: #555; }
            .progress-bar { height: 100%; width: 0; background: #007bff; transition: width .6s ease; }
            .question { margin: 40px 0 20px; font-size: 1.8em; }
            .options label { display: block; margin-bottom: 16px; font-size: 1.4em; }
            table { width: 100%; border-collapse: collapse; margin-top: 40px; font-size: 1.2em; }
            th, td { border: 1px solid #ccc; padding: 16px; text-align: left; }
            tr.wrong { background-color: #ffe6e6; }
            body.dark tr.wrong { background-color: #661111; }
            #darkModeToggle {
              position: absolute; top: 20px; right: 20px; padding: 10px 20px;
              background: #333; color: #fff; border: none; border-radius: 8px; cursor: pointer; font-size: 1em;
              transition: background .3s;
            }
            #darkModeToggle:hover { background: #555; }
    </style>
  </head>
  <body>
    <button id="darkModeToggle">深色模式 / Dark Mode</button>
    <a id="homeBtn" href="https://hisausage7.github.io/147test/" title="回首頁"
      >🏠 回首頁</a
    >

    <div id="container">
      <div id="welcome">
        <h1>147測驗M1校內考</h1>
        <div id="rules">
          <p><strong>考試注意事項 / Exam Rules:</strong></p>
          <P>!此章節沒有提供圖片題!
          </p>
            1. 請輸入姓名後才能開始作答。 / You must enter your name to start
            the quiz.
          </p>
          <p>
            2. 考試限時80分鐘，自動倒數。 / The quiz is timed for 80 minutes,
            countdown starts immediately.
          </p>
          <p>
            3. 作答途中可隨時點擊「離開考試」提前結束。 / You can click "Leave
            Quiz" anytime to finish early.
          </p>
          <p>
            4. 完成後會自動顯示所有答題結果與成績。 / Results and scores will be
            displayed after completion.
          </p>
          <p>
            5. 答對題目顯示O，答錯題目顯示X。 / Correct answers will show O,
            incorrect answers will show X.
          </p>
          <p>
            6. 測驗過程為亂序出題。 / The test process was chaotic and
            disordered in setting questions.
          </p>
          <p>!版權及源代碼所有-航機系008沈崑宸!</p>
          <p>!僅作為自我測驗使用!</p>
        </div>
        <input
          type="text"
          id="nameInput"
          placeholder="輸入姓名 / Enter your name"
          style="width:100%;padding:8px;margin-bottom:10px;font-size:1.4em;"
        />
        <input
          type="number"
          id="questionLimit"
          placeholder="輸入題數,至多75題 / Enter number of questions"
          style="width:100%;padding:8px;margin-bottom:10px;font-size:1.4em;"
        />
        <button id="startBtn" class="btn">開始測驗 / Start Quiz</button>
      </div>

      <div id="quiz" class="hidden">
        <div>
          <span id="welcomeName"></span>
          <span id="timer" style="float:right">80:00</span>
        </div>
        <div id="progress">
          題數: <span id="current">0</span> / <span id="total">0</span>
        </div>
        <div class="progress-container">
          <div id="progressBar" class="progress-bar"></div>
        </div>
        <div class="question" id="questionText"></div>
        <div class="options" id="options"></div>
        <button id="prevBtn" class="btn" style="background:#6c757d">
          上一題 / Previous
        </button>
        <button id="leaveBtn" class="btn">離開考試 / Leave Quiz</button>
      </div>

      <div id="results" class="hidden">
        <h2>測驗結果 / Results</h2>
        <div>
          <button id="retryBtn" class="btn">重新開始 / Retry</button>
          <button id="showWrongBtn" class="btn" style="background:#ffc107">
            只看錯題 / Wrong Only
          </button>
          <button id="showAllBtn" class="btn">看全部結果 / Show All</button>
        </div>
        <table>
          <thead>
            <tr>
              <th>題目</th>
              <th>您的答案</th>
              <th>正確答案</th>
              <th>結果</th>
            </tr>
          </thead>
          <tbody id="resultsBody"></tbody>
        </table>
        <div
          id="scoreSummary"
          style="text-align:center;margin-top:20px;font-size:1.2em"
        ></div>
      </div>
    </div>

    <script>
            document.addEventListener("DOMContentLoaded", function () {
              const questions = [
                // === PART 1 ===
      {
        question: "Eighteen thousandths, written as a decimal is:",
        options: ["A. 0.0018", "B. 0.018", "C. 0.18"],
        answer: "B"
      },
      {
        question: "40 divided by ⅛ is equal to:",
        options: ["A. 5", "B. 320", "C. 1/5"],
        answer: "B"
      },
      {
        question: "The next number in the sequence 1, 3, 6, 10 is:",
        options: ["A. 11", "B. 13", "C. 15"],
        answer: "C"
      },
      {
        question: "The value of [(-1)(-1)] -1 is:",
        options: ["A. -2", "B. -1", "C. 0"],
        answer: "B"
      },
      {
        question: "7 × 6 - 12÷3 + 1 is equal to:",
        options: ["A. 39", "B. 28", "C. -44"],
        answer: "A"
      },
      {
        question: "If £182.50 is shared equally between 5 people, how much would each person receive:",
        options: ["A. £35.50", "B. £37.50", "C. £36.50"],
        answer: "C"
      },
      {
        question: "The arithmetic mean of ten numbers is 36. If one of the numbers is 18, what is the mean of the other nine:",
        options: ["A. 32", "B. 36", "C. 38"],
        answer: "C"
      },
      {
        question: "Three thousand and forty nine written in numbers is:",
        options: ["A. 3,490", "B. 30049", "C. 3049"],
        answer: "C"
      },
      {
        question: "If the fractions 2/5, 3/7 and 1/3 are arranged in order of size, smallest first, the order would be:",
        options: ["A. 2/5, 1/3, 3/7", "B. 1/3, 2/5, 3/7", "C. 3/7, 2/5, 1/3"],
        answer: "B"
      },
      {
        question: "3⅔ + 4⅗ is equal to:",
        options: ["A. 7⅓", "B. 6¹³/₁₅", "C. 8⁴/₁₅"],
        answer: "C"
      },
      {
        question: "2½ × 1⅓ is equal to:",
        options: ["A. 2⅕", "B. 2⅙", "C. 3⅓"],
        answer: "C"
      },
      {
        question: "⅚ ÷ ⅓ is equal to:",
        options: ["A. ⁵/₂", "B. ⁵/₁₈", "C. 2½"],
        answer: "C"
      },
      {
        question: "The number 46700 when written in Standard Form is:",
        options: ["A. 46.7 × 10³", "B. 4.67 × 10⁴", "C. 4.67 × 10⁵"],
        answer: "B"
      },
      {
        question: "When written in Standard Form 0.00075 is equal to:",
        options: ["A. 75 × 10⁻⁵", "B. 7.5 × 10⁻⁴", "C. 0.75 × 10⁻³"],
        answer: "B"
      },
      {
        question: "3 × 10² × 2 × 10⁴ is equal to:",
        options: ["A. 6×10⁸", "B. 6×10⁶", "C. 6×10⁻²"],
        answer: "B"
      },
      {
        question: "4 × 10⁶ ÷ 2 × 10³ is equal to:",
        options: ["A. 2 × 10²", "B. 2 × 10³", "C. 2 × 10⁻³"],
        answer: "B"
      },
      {
        question: "Which of the following is a prime number:",
        options: ["A. 15", "B. 27", "C. 41"],
        answer: "C"
      },
      {
        question: "2, 3 and 5 are the factors of:",
        options: ["A. 6", "B. 10", "C. 30"],
        answer: "C"
      },
      {
        question: "The HCF of 20, 30 and 60 is:",
        options: ["A. 2", "B. 10", "C. 20"],
        answer: "B"
      },
      {
        question: "The LCM of 2, 4, 5 and 6 is:",
        options: ["A. 240", "B. 60", "C. 6"],
        answer: "B"
      },
      {
        question: "If 1 km = 0.6 miles, then 66 miles is equivalent to:",
        options: ["A. 110 km", "B. 1100 km", "C. 11 km"],
        answer: "A"
      },
      {
        question: "If £120 is divided in the ratio 2:3, then the larger share is:",
        options: ["A. £48", "B. £80", "C. £72"],
        answer: "C"
      },
      {
        question: "If 50% of a certain length is 500 mm, the complete length is:",
        options: ["A. 250 mm", "B. 1000 mm", "C. 100 mm"],
        answer: "B"
      },
      {
        question: "What is the square root of 16 × 64:",
        options: ["A. 40", "B. 32", "C. 256"],
        answer: "B"
      },
      {
        question: "The difference between 2³ and 3² is:",
        options: ["A. 9", "B. 1", "C. 17"],
        answer: "B"
      },
      {
        question: "What is 0.0059 correct to 2 decimal places:",
        options: ["A. 0.01", "B. 0.10", "C. 0.006"],
        answer: "A"
      },
      {
        question: "Correct to 2 significant figures 3.0394 is:",
        options: ["A. 3.0", "B. 3.04", "C. 3.03"],
        answer: "A"
      },
      {
        question: "How many square centimetres are there in a square metre:",
        options: ["A. 100", "B. 1000", "C. 10,000"],
        answer: "C"
      },
      {
        question: "A triangle has an altitude of 50 mm and a base of 20 mm. Its area is:",
        options: ["A. 250 mm²", "B. 0.25 cm²", "C. 500 mm²"],
        answer: "C"
      },
      {
        question: "Oil is sold in a closed cylindrical container whose diameter is 7 cm and whose height is 10 cm. How much oil does the can hold:",
        options: ["A. Less than 0.4 litres", "B. 0.5 litres", "C. More than 1 litre"],
        answer: "A"
      },
      // === PART 2 ===
      {
        question: "Three times a certain number x plus five is equal to five times the number plus two. The correct algebraic expression for this is:",
        options: ["A. 3x +5 = 5+ x +2", "B. 3+x +5 = 5x +2", "C. 3x +5 = 5x +2"],
        answer: "C"
      },
      {
        question: "(3x + 5) - (x + 3) is equal to:",
        options: ["A. 2x + 2", "B. 2x - 8", "C. 2x - 2"],
        answer: "A"
      },
      {
        question: "Which of the following is NOT equal to ⅓xy:",
        options: ["A. xy/3", "B. x/3y", "C. 1/3yx"],
        answer: "B"
      },
      {
        question: "If p = 3 and q = 4, then q² - p² is equal to:",
        options: ["A. 7", "B. -7", "C. 1"],
        answer: "A"
      },
      {
        question: "When the brackets are removed from 2(3p - 2q) the answer is:",
        options: ["A. 23p - 22q", "B. 6p - 4q", "C. 6p + 4q"],
        answer: "B"
      },
      {
        question: "When 5x + 3x - 4x is simplified, the answer is:",
        options: ["A. 12x", "B. 4x", "C. -4x"],
        answer: "B"
      },
      {
        question: "When 8a² is divided by 2a², the answer is:",
        options: ["A. 4a²", "B. 4a", "C. 4"],
        answer: "C"
      },
      {
        question: "When 4x + 8y is completely factorised, the correct answer is:",
        options: ["A. 4(x + y)", "B. 4(x + 2y)", "C. 4(2x + 2y)"],
        answer: "B"
      },
      {
        question: "When the equation 3x - 8 = 19 is solved, the value of x is:",
        options: ["A. 8", "B. 7", "C. 9"],
        answer: "C"
      },
      {
        question: "When (x + 5)(x + 2) is expanded and simplified, the answer is:",
        options: ["A. 2x + 7", "B. x² + 10", "C. x² + 7x + 10"],
        answer: "C"
      },
      {
        question: "When c is made the subject of the formula bc²/d = a, the answer is:",
        options: ["A. c = da/b", "B. c = √a - d/b", "C. c = √(ad/b)"],
        answer: "C"
      },
      {
        question: "When x² - 9 is factorised, the answer is:",
        options: ["A. (x - 3)", "B. (x - 3)(x - 3)", "C. (x - 3)(x + 3)"],
        answer: "C"
      },
      {
        question: "Log a/b is exactly the same as:",
        options: ["A. log(a - b)", "B. log a - log b", "C. log a / log b"],
        answer: "B"
      },
      {
        question: "If log₁₀2 = 0.3010, then log₁₀2000 is:",
        options: ["A. 2.3010", "B. 3.3010", "C. 301"],
        answer: "B"
      },
      {
        question: "58₁₀ expressed in Binary is:",
        options: ["A. 111001", "B. 111010", "C. 101111"],
        answer: "B"
      },
      {
        question: "In common logarithmic form the characteristic of the number 0.002968 is:",
        options: ["A. /2", "B. /3", "C. 2.968"],
        answer: "B"
      },
      {
        question: "The value of x in log₅125 = x is:",
        options: ["A. 5", "B. 25", "C. 3"],
        answer: "C"
      },
      {
        question: "The binary number 1110111₂ expressed as a Base₁₀ (Denary) number is:",
        options: ["A. 121", "B. 119", "C. 117"],
        answer: "B"
      },
      {
        question: "When the Octal (Base 8) numbers 37 and 42 are added together, the answer is:",
        options: ["A. 79₈", "B. 101₈", "C. 110₈"],
        answer: "B"
      },
      {
        question: "When the Hexadecimal (Base 16) numbers 35₁₆ and 48₁₆ are added, the correct answer is:",
        options: ["A. 83₁₆", "B. 713", "C. 7D"],
        answer: "C"
      },
      {
        question: "The decimal value 625 coded in BCD is:",
        options: ["A. 0110 0010 0100", "B. 0110 0010 0101", "C. 0110 0010 0111"],
        answer: "B"
      },
      {
        question: "In the simultaneous equations x + y = 6, x - y = 2, if y = 2 then x is:",
        options: ["A. 3", "B. 5", "C. 4"],
        answer: "C"
      },
      {
        question: "When x² - 2x - 8 is factorised, the correct equation is:",
        options: ["A. (x - 2)(x - 4)", "B. (x + 2)(x + 4)", "C. (x + 2)(x - 4)"],
        answer: "C"
      },
      {
        question: "The logarithm of two numbers multiplied together may be found by:",
        options: ["A. Adding the logarithms of the two numbers together", "B. Multiplying the logarithms together", "C. Subtracting the logarithms of the two numbers"],
        answer: "A"
      },
      {
        question: "a⁵ × a⁶ is equal to:",
        options: ["A. a³⁰", "B. a¹¹", "C. a¹⁵"],
        answer: "B"
      },
      {
        question: "x⁹ / x² is equal to:",
        options: ["A. x¹⁸", "B. x¹¹", "C. x⁷"],
        answer: "C"
      },
      {
        question: "1/√x is equal to:",
        options: ["A. x¹ᐟ²", "B. x⁻¹ᐟ²", "C. x²"],
        answer: "B"
      },
      {
        question: "125⁰ is equal to:",
        options: ["A. 125⁰", "B. δ", "C. 1"],
        answer: "C"
      },
      {
        question: "1/9¹ᐟ² is equal to:",
        options: ["A. 1/3", "B. 1/4.5", "C. 81"],
        answer: "A"
      },
      // === PART 3 ===
      {
        question: "Which of the following equations represents a linear equation:",
        options: ["A. y = x² - 2", "B. y = √x + 1", "C. y = 3 - 8x"],
        answer: "C"
      },
      {
        question: "Of the following three pairs of equations, all representing straight lines, which pair are parallel to each other:",
        options: ["A. y = 3x + 2, y = -3x - 2", "B. y = 4x + 1, y = 1/4x + 1", "C. y = -5x + 1, y = 7 - 5x"],
        answer: "C"
      },
      {
        question: "What is the gradient of the line represented by the equation 3x - 5y = 5:",
        options: ["A. 2/3", "B. 3/5", "C. -2/3"],
        answer: "B"
      },
      {
        question: "At what point does the straight line represented by the equation y = 7 - 5x cross the y-axis:",
        options: ["A. -7", "B. -5", "C. 7"],
        answer: "C"
      },
      {
        question: "The equation 5y = 5x - 3 and y = 7 + 5x give rise to straight lines. Are these lines:",
        options: ["A. Perpendicular to each other", "B. Parallel", "C. Neither parallel nor perpendicular"],
        answer: "B"
      },
      {
        question: "Which of the following equations would NOT produce a quadratic graph:",
        options: ["A. y = x²", "B. y = x³ + 1", "C. y = x² - 3x"],
        answer: "B"
      },
      {
        question: "What type of graph would the equation y = x³ - x² - 4x + 4 produce:",
        options: ["A. Linear", "B. Cubic", "C. Quadratic"],
        answer: "B"
      },
      {
        question: "A triangle which has two equal sides is called an:",
        options: ["A. Equilateral triangle", "B. Isosceles triangle", "C. Scalene triangle"],
        answer: "B"
      },
      {
        question: "An obtuse angled triangle has:",
        options: ["A. One angle greater than 90°", "B. One angle greater than 180°", "C. No angles greater than 90°"],
        answer: "A"
      },
      {
        question: "The area of a Trapezium is equal to:",
        options: ["A. Sum of parallel sides times the height", "B. One half the sum of the parallel sides times the height", "C. One half the sum of the parallel sides times one half the height"],
        answer: "B"
      },
      {
        question: "A right angled triangle has two sides, other than the hypotenuse, whose lengths are 5 units and 12 units. The length of the hypotenuse is:",
        options: ["A. 13 units", "B. 7 units", "C. 3 units"],
        answer: "A"
      },
      {
        question: "The angle 120° expressed in radians is:",
        options: ["A. π", "B. π/3", "C. 2π/3"],
        answer: "C"
      },
      {
        question: "Angles that add up to 90° are called:",
        options: ["A. Complementary", "B. Supplementary", "C. Subordinate"],
        answer: "A"
      },
      {
        question: "How many degrees is π radians equal to:",
        options: ["A. 360°", "B. 90°", "C. 180°"],
        answer: "C"
      },
      {
        question: "In a circle of radius r, where θ is the angle subtended by the arc at the centre, the correct formula for the area of the sector so formed is:",
        options: ["A. πrθ", "B. 1/2πθ", "C. 1/2πr²θ"],
        answer: "C"
      },
      {
        question: "Two triangles are said to be similar if:",
        options: ["A. The three sides of one are equal to the three sides of the other", "B. The three angles of one are equal to the three angles of the other", "C. One angle and one side of one are equal to one angle and one side of the other"],
        answer: "B"
      },


              ];

              function shuffle(array) {
                for (let i = array.length - 1; i > 0; i--) {
                  const j = Math.floor(Math.random() * (i + 1));
                  [array[i], array[j]] = [array[j], array[i]];
                }
                return array;
              }

              let shuffledQuestions;
              let current = 0, total = 0, timer = 80 * 60, interval, answers = [];

              function fmtTime(s) {
                const m = Math.floor(s / 60).toString().padStart(2, "0");
                const sec = (s % 60).toString().padStart(2, "0");
                return m + ":" + sec;
              }

              const startBtn = document.getElementById("startBtn");
              const prevBtn = document.getElementById("prevBtn");
              const leaveBtn = document.getElementById("leaveBtn");
              const retryBtn = document.getElementById("retryBtn");
              const showWrongBtn = document.getElementById("showWrongBtn");
              const showAllBtn = document.getElementById("showAllBtn");
              const darkModeToggle = document.getElementById("darkModeToggle");
              const progressBar = document.getElementById("progressBar");

              startBtn.addEventListener("click", () => {
                const n = document.getElementById("nameInput").value.trim();
                const qLimit = parseInt(document.getElementById("questionLimit").value);

                if (!n) return alert("請輸入姓名 / Enter your name");
                if (!qLimit || qLimit <= 0) return alert("請輸入要作答的題數,最多105題 / Enter number of questions");

                shuffledQuestions = shuffle([...questions]).slice(0, Math.min(qLimit, questions.length));
                total = shuffledQuestions.length;
                current = 0; answers = []; timer = 80 * 60;

                document.getElementById("welcome").classList.add("hidden");
                document.getElementById("quiz").classList.remove("hidden");
                document.getElementById("welcomeName").innerText = "歡迎: " + n;
                document.getElementById("total").innerText = total;
                updateProgress();

                interval = setInterval(() => {
                  if (timer > 0) {
                    timer--;
                    document.getElementById("timer").innerText = fmtTime(timer);
                  } else {
                    clearInterval(interval);
                    finish();
                  }
                }, 1000);

                showQ();
              });

              prevBtn.addEventListener("click", () => {
                if (current > 0) {
                  current--;
                  answers.pop();
                  showQ();
                }
              });

              leaveBtn.addEventListener("click", finish);
              retryBtn.addEventListener("click", () => location.reload());
              showWrongBtn.addEventListener("click", filterResultsWrong);
              showAllBtn.addEventListener("click", showAllResults);
              darkModeToggle.addEventListener("click", () => document.body.classList.toggle("dark"));

              function showQ() {
                if (current >= total) return finish();
                document.getElementById("current").innerText = current + 1;
                updateProgress();

                const q = shuffledQuestions[current];
                document.getElementById("questionText").innerText = q.question;

                const optDiv = document.getElementById("options");
                optDiv.innerHTML = "";

                let optionsWithFlag = q.options.map((option) => ({
                  text: option,
                  isAnswer: option.charAt(0) === q.answer,
                }));
                optionsWithFlag = shuffle(optionsWithFlag);

                optionsWithFlag.forEach((opt) => {
                  const lbl = document.createElement("label");
                  const rd = document.createElement("input");
                  rd.type = "radio";
                  rd.name = "opt";
                  rd.value = opt.text;
                  rd.onchange = () => {
                    answers.push({
                      q,
                      selectedText: opt.text,
                      correctText: q.options.find((optItem) => optItem.charAt(0) === q.answer),
                      correct: opt.isAnswer,
                    });
                    current++;
                    showQ();
                  };
                  lbl.append(rd, " ", opt.text);
                  optDiv.append(lbl);
                });
              }

              function updateProgress() {
                const percent = (current / total) * 100;
                progressBar.style.width = percent + "%";
              }

              function finish() {
                clearInterval(interval);
                document.getElementById("quiz").classList.add("hidden");
                document.getElementById("results").classList.remove("hidden");
                renderResults(answers);
                document.getElementById("scoreSummary").innerText =
                  `答對 ${answers.filter((a) => a.correct).length} 題 / 已作答 ${answers.length} 題 / 共 ${total} 題`;
                window.scrollTo({ top: 0, behavior: "smooth" });
              }

              function renderResults(data) {
                const tb = document.getElementById("resultsBody");
                tb.innerHTML = "";
                data.forEach((a) => {
                  const tr = document.createElement("tr");
                  tr.innerHTML = `
                    <td>${a.q.question}</td>
                    <td>${a.selectedText}</td>
                    <td>${a.correctText}</td>
                    <td>${a.correct ? "O" : "X"}</td>
                  `;
                  if (!a.correct) tr.classList.add("wrong");
                  tb.append(tr);
                });
              }

              function filterResultsWrong() { renderResults(answers.filter((a) => !a.correct)); }
              function showAllResults() { renderResults(answers); }
            });
    </script>
  </body>
</html>
