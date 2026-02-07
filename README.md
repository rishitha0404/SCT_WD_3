# SCT_WD_3
Quiz game application
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Interactive Quiz Game</title>

  <style>
    body {
      font-family: Arial, sans-serif;
      background: #1f2933;
      color: #ffffff;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
    }

    .quiz-box {
      background: #323f4b;
      width: 420px;
      padding: 25px;
      border-radius: 10px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.4);
    }

    h2 {
      text-align: center;
      margin-bottom: 20px;
    }

    .question {
      font-size: 18px;
      margin-bottom: 15px;
    }

    .options label {
      display: block;
      margin-bottom: 10px;
      cursor: pointer;
    }

    input[type="text"] {
      width: 100%;
      padding: 8px;
      border-radius: 5px;
      border: none;
      margin-top: 8px;
    }

    button {
      width: 100%;
      padding: 10px;
      background: #38bdf8;
      border: none;
      border-radius: 5px;
      font-size: 16px;
      margin-top: 15px;
      cursor: pointer;
    }

    button:hover {
      background: #0ea5e9;
    }

    .score {
      text-align: center;
      font-size: 20px;
    }
  </style>
</head>

<body>

<div class="quiz-box">
  <h2>Quiz Game</h2>
  <div id="quiz"></div>
  <button id="nextBtn">Next</button>
</div>

<script>
  const quizData = [
    {
      type: "single",
      question: "Which language is mainly used to style web pages?",
      options: ["HTML", "Python", "CSS", "C"],
      answer: "CSS"
    },
    {
      type: "multiple",
      question: "Select all programming languages:",
      options: ["HTML", "Java", "Python", "CSS"],
      answer: ["Java", "Python"]
    },
    {
      type: "fill",
      question: "JavaScript is used to make web pages ________.",
      answer: "interactive"
    }
  ];

  let currentQuestion = 0;
  let score = 0;

  const quiz = document.getElementById("quiz");
  const nextBtn = document.getElementById("nextBtn");

  loadQuestion();

  function loadQuestion() {
    quiz.innerHTML = "";
    const q = quizData[currentQuestion];

    const questionEl = document.createElement("div");
    questionEl.className = "question";
    questionEl.textContent = q.question;
    quiz.appendChild(questionEl);

    const optionsEl = document.createElement("div");
    optionsEl.className = "options";

    if (q.type === "single") {
      q.options.forEach(option => {
        optionsEl.innerHTML += `
          <label>
            <input type="radio" name="answer" value="${option}"> ${option}
          </label>
        `;
      });
    }

    if (q.type === "multiple") {
      q.options.forEach(option => {
        optionsEl.innerHTML += `
          <label>
            <input type="checkbox" value="${option}"> ${option}
          </label>
        `;
      });
    }

    if (q.type === "fill") {
      optionsEl.inne

