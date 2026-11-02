# blooket-hacks.
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="theme-color" content="#6558e8">
  <title>Quiz Quest — Play, learn, level up</title>
  <style>
    :root {
      color-scheme: light;
      --ink: #24233a;
      --muted: #77768d;
      --purple: #6558e8;
      --purple-dark: #4e43c4;
      --surface: #fff;
      --line: #e9e8f2;
      --green: #23845d;
      --red: #c84e64;
      font-family: Inter, ui-rounded, "Segoe UI", system-ui, -apple-system, sans-serif;
    }
    * { box-sizing: border-box; }
    body {
      min-height: 100vh;
      margin: 0;
      color: var(--ink);
      background: radial-gradient(ellipse at 12% 8%, #eceaff 0, transparent 34%),
                  radial-gradient(ellipse at 90% 86%, #e0f8f2 0, transparent 30%), #f8f8fc;
    }
    button { font: inherit; }
    .topbar { display: flex; justify-content: space-between; align-items: center; max-width: 1080px; margin: auto; padding: 22px 24px; }
    .brand { display: flex; align-items: center; gap: 10px; font-size: 1.15rem; font-weight: 850; letter-spacing: -.04em; }
    .brand-mark { display: grid; place-items: center; width: 38px; height: 38px; border-radius: 13px; color: white; background: var(--purple); box-shadow: 0 7px 16px #6558e844; }
    .top-note { color: var(--muted); font-size: .88rem; }
    main { width: min(760px, calc(100% - 32px)); margin: 46px auto 70px; }
    .eyebrow { margin: 0 0 9px; color: var(--purple); font-weight: 800; font-size: .78rem; letter-spacing: .13em; text-transform: uppercase; }
    h1 { margin: 0; font-size: clamp(2rem, 5vw, 3.2rem); letter-spacing: -.06em; line-height: 1.08; }
    .intro { margin: 13px 0 27px; color: var(--muted); line-height: 1.6; }
    .card { padding: clamp(20px, 5vw, 34px); border: 1px solid #eeedf5; border-radius: 25px; background: var(--surface); box-shadow: 0 20px 55px #302c6410; }
    .setup-row { display: flex; flex-wrap: wrap; align-items: end; gap: 14px; }
    .field { flex: 1 1 210px; }
    label { display: block; margin-bottom: 8px; color: #55546a; font-weight: 750; font-size: .88rem; }
    select { width: 100%; padding: 13px 14px; border: 1px solid var(--line); border-radius: 12px; color: var(--ink); background: white; font: inherit; }
    .primary, .secondary { border: 0; border-radius: 12px; padding: 13px 20px; cursor: pointer; font-weight: 800; transition: transform .15s, background .15s; }
    .primary { color: white; background: var(--purple); box-shadow: 0 7px 15px #6558e833; }
    .primary:hover { background: var(--purple-dark); transform: translateY(-1px); }
    .secondary { color: var(--purple-dark); background: #f0efff; }
    .secondary:hover { background: #e7e5ff; }
    button:focus-visible, select:focus-visible { outline: 3px solid #a9a2ff; outline-offset: 3px; }
    .stats { display: flex; gap: 10px; margin-top: 20px; }
    .stat { flex: 1; padding: 13px 15px; border-radius: 14px; background: #f8f7fc; }
    .stat strong { display: block; font-size: 1.05rem; }
    .stat span { color: var(--muted); font-size: .78rem; }
    .game { display: none; }
    .game.active { display: block; }
    .game-head { display: flex; justify-content: space-between; align-items: center; gap: 12px; margin-bottom: 20px; color: var(--muted); font-size: .9rem; font-weight: 700; }
    .progress { height: 9px; overflow: hidden; margin-bottom: 28px; border-radius: 99px; background: #efeff5; }
    .progress > div { width: 0; height: 100%; border-radius: inherit; background: linear-gradient(90deg, #8277f7, #5c50dd); transition: width .3s ease; }
    .question { margin: 0 0 23px; font-size: clamp(1.35rem, 3vw, 1.8rem); line-height: 1.35; letter-spacing: -.035em; }
    .answers { display: grid; gap: 11px; }
    .answer { display: flex; align-items: center; width: 100%; min-height: 56px; padding: 12px 15px; border: 1px solid var(--line); border-radius: 14px; color: var(--ink); background: white; text-align: left; cursor: pointer; transition: border .15s, background .15s, transform .15s; }
    .answer:hover:not(:disabled) { border-color: #aaa3ff; background: #fbfaff; transform: translateY(-1px); }
    .answer .letter { display: grid; place-items: center; flex: 0 0 30px; width: 30px; height: 30px; margin-right: 12px; border-radius: 9px; color: #716f83; background: #f2f1f7; font-size: .82rem; font-weight: 850; }
    .answer.correct { border-color: #8bd1b2; background: #f0fbf6; }
    .answer.correct .letter { color: white; background: var(--green); }
    .answer.wrong { border-color: #edacb7; background: #fff5f6; }
    .answer.wrong .letter { color: white; background: var(--red); }
    .answer:disabled { cursor: default; }
    .feedback { min-height: 28px; margin: 14px 0 4px; font-weight: 750; }
    .feedback.good { color: var(--green); }
    .feedback.bad { color: var(--red); }
    .game-actions { display: flex; justify-content: flex-end; margin-top: 12px; }
    .results { display: none; text-align: center; }
    .results.active { display: block; }
    .result-icon { display: grid; place-items: center; width: 72px; height: 72px; margin: 0 auto 15px; border-radius: 23px; background: #f0efff; font-size: 2rem; }
    .results h2 { margin: 0; font-size: 2rem; letter-spacing: -.05em; }
    .results p { color: var(--muted); line-height: 1.6; }
    .score { margin: 12px 0; color: var(--purple); font-size: 3.7rem; font-weight: 900; letter-spacing: -.07em; }
    .results .primary { margin-top: 8px; }
    .custom-wrap { margin-top: 17px; }
    details { border: 1px solid #eeedf5; border-radius: 16px; background: #ffffffb8; }
    summary { padding: 16px 18px; cursor: pointer; font-weight: 800; }
    .custom-content { padding: 0 18px 18px; }
    .custom-content p { margin: 0 0 10px; color: var(--muted); font-size: .88rem; line-height: 1.5; }
    textarea { display: block; width: 100%; min-height: 135px; resize: vertical; padding: 12px; border: 1px solid var(--line); border-radius: 12px; font: .85rem/1.5 ui-monospace, SFMono-Regular, Menlo, monospace; }
    .custom-controls { display: flex; flex-wrap: wrap; align-items: center; gap: 10px; margin-top: 10px; }
    .custom-status { color: var(--muted); font-size: .85rem; }
    footer { padding: 0 20px 28px; color: #8b899d; text-align: center; font-size: .8rem; }
    @media (max-width: 520px) { .topbar { padding: 17px 18px; } main { margin-top: 28px; } .top-note { font-size: .76rem; } .setup-row .primary { width: 100%; } .stats { gap: 7px; } .stat { padding: 11px; } }
  </style>
</head>
<body>
  <header class="topbar">
    <div class="brand"><span class="brand-mark" aria-hidden="true">✦</span> Quiz Quest</div>
    <div class="top-note">A little play. A lot of learning.</div>
  </header>
  <main>
    <section id="welcome">
      <p class="eyebrow">Your next brain break</p>
      <h1>Ready, set, <span style="color:var(--purple)">quiz!</span></h1>
      <p class="intro">Pick a topic, answer at your own pace, and see how you did. Want to practice your own material? Add a custom quiz below.</p>
      <div class="card">
        <div class="setup-row">
          <div class="field"><label for="category">Choose a topic</label><select id="category"><option value="mix">Mixed bag</option><option value="science">Science</option><option value="space">Space</option><option value="words">Words &amp; language</option></select></div>
          <button class="primary" id="start">Start playing <span aria-hidden="true">→</span></button>
        </div>
        <div class="stats">
          <div class="stat"><strong>🧠 Learn</strong><span>Useful little facts</span></div>
          <div class="stat"><strong>✨ Explore</strong><span>Questions for everyone</span></div>
          <div class="stat"><strong>🔒 Just for you</strong><span>No account needed</span></div>
        </div>
      </div>
      <div class="custom-wrap">
        <details>
          <summary>Make a quiz with my own questions</summary>
          <div class="custom-content">
            <p>Enter one question per line in this format: <code>Question | correct answer | wrong answer 1 | wrong answer 2</code>. Your quiz stays in this browser tab.</p>
            <textarea id="customQuestions" aria-label="Custom quiz questions" placeholder="What is 2 + 2? | 4 | 3 | 5&#10;Which planet is known as the Red Planet? | Mars | Venus | Jupiter"></textarea>
            <div class="custom-controls"><button class="secondary" id="loadCustom">Use my questions</button><span class="custom-status" id="customStatus" aria-live="polite"></span></div>
          </div>
        </details>
      </div>
    </section>

    <section class="card game" id="game" aria-live="polite">
      <div class="game-head"><span id="questionCount">Question 1 of 5</span><span id="scoreLabel">⭐ 0 points</span></div>
      <div class="progress" aria-label="Quiz progress"><div id="progressBar"></div></div>
      <h2 class="question" id="questionText"></h2>
      <div class="answers" id="answers"></div>
      <p class="feedback" id="feedback" aria-live="assertive"></p>
      <div class="game-actions"><button class="primary" id="next" hidden>Next question →</button></div>
    </section>

    <section class="card results" id="results" aria-live="polite">
      <div class="result-icon" id="resultIcon">🏆</div>
      <p class="eyebrow">Quiz complete</p>
      <h2 id="resultTitle">Nice work!</h2>
      <div class="score" id="finalScore">0/5</div>
      <p id="resultMessage"></p>
      <button class="primary" id="playAgain">Play again</button>
    </section>
  </main>
  <footer>Quiz Quest is an independent practice game and is not affiliated with any other quiz platform.</footer>
  <script>
    const questionBank = {
      science: [
        { q: 'What gas do plants absorb from the air during photosynthesis?', a: 'Carbon dioxide', options: ['Carbon dioxide', 'Oxygen', 'Hydrogen', 'Helium'] },
        { q: 'What is the hardest naturally occurring substance?', a: 'Diamond', options: ['Granite', 'Iron', 'Diamond', 'Quartz'] },
        { q: 'Which part of a cell contains most of its genetic material?', a: 'The nucleus', options: ['The membrane', 'The nucleus', 'The ribosome', 'The cytoplasm'] },
        { q: 'At sea level, what is the boiling point of water in Celsius?', a: '100°C', options: ['0°C', '50°C', '100°C', '150°C'] },
        { q: 'Which force keeps planets in orbit around the Sun?', a: 'Gravity', options: ['Magnetism', 'Friction', 'Gravity', 'Electricity'] }
      ],
      space: [
        { q: 'Which planet is known as the Red Planet?', a: 'Mars', options: ['Venus', 'Mars', 'Jupiter', 'Mercury'] },
        { q: 'What is the name of the galaxy that contains our Solar System?', a: 'The Milky Way', options: ['Andromeda', 'The Milky Way', 'Whirlpool', 'Sombrero'] },
        { q: 'Which is the largest planet in our Solar System?', a: 'Jupiter', options: ['Saturn', 'Neptune', 'Earth', 'Jupiter'] },
        { q: 'What star is at the center of our Solar System?', a: 'The Sun', options: ['Polaris', 'Sirius', 'The Sun', 'Betelgeuse'] },
        { q: 'Which planet is famous for its prominent rings?', a: 'Saturn', options: ['Mars', 'Saturn', 'Venus', 'Mercury'] }
      ],
      words: [
        { q: 'Which word is a synonym for “curious”?', a: 'Inquisitive', options: ['Inquisitive', 'Sleepy', 'Silent', 'Careless'] },
        { q: 'What is the plural of “mouse”?', a: 'Mice', options: ['Mouses', 'Mices', 'Mice', 'Mouse'] },
        { q: 'Which of these is a verb?', a: 'To discover', options: ['Bright', 'To discover', 'Happiness', 'Quickly'] },
        { q: 'What punctuation mark usually ends a question?', a: 'Question mark', options: ['Comma', 'Period', 'Question mark', 'Colon'] },
        { q: 'What does the prefix “re-” often mean?', a: 'Again', options: ['Before', 'Under', 'Again', 'Between'] }
      ]
    };
    const $ = (id) => document.getElementById(id);
    let questions = [], index = 0, score = 0, customBank = null;

    function shuffled(items) { return [...items].sort(() => Math.random() - 0.5); }
    function startQuiz() {
      const choice = $('category').value;
      const bank = customBank || (choice === 'mix' ? Object.values(questionBank).flat() : questionBank[choice]);
      questions = shuffled(bank).slice(0, Math.min(5, bank.length));
      index = 0; score = 0;
      $('welcome').hidden = true;
      $('results').classList.remove('active');
      $('game').classList.add('active');
      renderQuestion();
    }
    function renderQuestion() {
      const item = questions[index];
      $('questionCount').textContent = `Question ${index + 1} of ${questions.length}`;
      $('scoreLabel').textContent = `⭐ ${score} ${score === 1 ? 'point' : 'points'}`;
      $('progressBar').style.width = `${(index / questions.length) * 100}%`;
      $('questionText').textContent = item.q;
      $('feedback').textContent = '';
      $('feedback').className = 'feedback';
      $('next').hidden = true;
      $('answers').replaceChildren();
      shuffled(item.options).forEach((option, i) => {
        const button = document.createElement('button');
        button.className = 'answer';
        button.innerHTML = `<span class="letter">${String.fromCharCode(65 + i)}</span>`;
        const label = document.createElement('span');
        label.textContent = option;
        button.append(label);
        button.addEventListener('click', () => chooseAnswer(button, option, item));
        $('answers').append(button);
      });
    }
    function chooseAnswer(selected, answer, item) {
      const correct = answer === item.a;
      $('answers').querySelectorAll('button').forEach(button => {
        button.disabled = true;
        if (button.textContent.slice(1).trim() === item.a) button.classList.add('correct');
      });
      if (correct) {
        score++;
        $('feedback').textContent = 'That’s right! Great job. 🎉';
        $('feedback').classList.add('good');
      } else {
        selected.classList.add('wrong');
        $('feedback').textContent = `Not quite — the answer is ${item.a}. Keep going!`;
        $('feedback').classList.add('bad');
      }
      $('scoreLabel').textContent = `⭐ ${score} ${score === 1 ? 'point' : 'points'}`;
      $('next').textContent = index === questions.length - 1 ? 'See my score →' : 'Next question →';
      $('next').hidden = false;
    }
    function finishQuiz() {
      $('game').classList.remove('active');
      $('progressBar').style.width = '100%';
      $('results').classList.add('active');
      $('finalScore').textContent = `${score}/${questions.length}`;
      const ratio = score / questions.length;
      $('resultIcon').textContent = ratio === 1 ? '🏆' : ratio >= .6 ? '🌟' : '🌱';
      $('resultTitle').textContent = ratio === 1 ? 'Perfect score!' : ratio >= .6 ? 'Nice work!' : 'Good practice!';
      $('resultMessage').textContent = ratio === 1 ? 'You got every question right. You’re on a roll!' : 'Every round is a chance to learn something new. Want to try again?';
    }
    $('start').addEventListener('click', startQuiz);
    $('next').addEventListener('click', () => { if (index < questions.length - 1) { index++; renderQuestion(); } else finishQuiz(); });
    $('playAgain').addEventListener('click', () => { $('welcome').hidden = false; $('results').classList.remove('active'); $('category').focus(); });
    $('loadCustom').addEventListener('click', () => {
      const lines = $('customQuestions').value.split('\n').map(line => line.trim()).filter(Boolean);
      const parsed = lines.map(line => line.split('|').map(part => part.trim())).filter(parts => parts.length >= 3 && parts[0] && parts[1] && parts.slice(1).filter(Boolean).length >= 3).map(parts => ({ q: parts[0], a: parts[1], options: parts.slice(1).filter(Boolean) }));
      if (!parsed.length) { $('customStatus').textContent = 'Add at least one valid question with a correct answer and two distractors.'; customBank = null; return; }
      customBank = parsed;
      $('customStatus').textContent = `${parsed.length} question${parsed.length === 1 ? '' : 's'} ready! Press “Start playing” to begin.`;
      $('category').value = 'mix';
    });
  </script>
</body>
</html>

README.md

md
# Quiz Quest

A cheerful, standalone quiz-practice game that runs entirely in your browser. Choose a built-in topic or enter your own questions, then answer at your own pace and see your score.

## Run it

Open `index.html` in a browser. No install, account, server, or external services are required.

## Custom questions

On the page, open **Make a quiz with my own questions** and enter one question per line:

`Question | correct answer | wrong answer 1 | wrong answer 2`

This is an independent practice game and does not
