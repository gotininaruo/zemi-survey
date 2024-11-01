# zemi-survey
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>時給アンケート</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .question {
            margin-bottom: 15px;
        }
    </style>
    <script>
        function getRandomX() {
            const values = [1000, 1050, 1100, 1150, 1200, 1250, 1300, 1350, 1400, 1450, 1500, 1550, 1600];
            return values[Math.floor(Math.random() * values.length)];
        }

        function getRandomY() {
            const values = [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100];
            return values[Math.floor(Math.random() * values.length)];
        }

        function loadSurvey() {
            const surveyContainer = document.getElementById('surveyContainer');
            surveyContainer.innerHTML = '';  // コンテナをリセット

            // 6問のアンケートを生成
            for (let i = 0; i < 6; i++) {
                const xValue = getRandomX();  // ランダムな時給
                const yValue = getRandomY();  // ランダムな確率

                const question = document.createElement('div');
                question.classList.add('question'); // スタイル用のクラス追加
                question.innerHTML = `
                    <p>時給${xValue}円でシフトに入れる確率が${yValue}%の場合に働きたいですか？</p>
                    <label>
                        <input type="radio" name="answer${i}" value="はい"> はい
                    </label>
                    <label>
                        <input type="radio" name="answer${i}" value="いいえ"> いいえ
                    </label>
                `;
                surveyContainer.appendChild(question); // 質問を追加
            }
        }

        // ページが読み込まれたらアンケートを表示
        window.onload = loadSurvey;
    </script>
</head>
<body>
    <h1>時給アンケート</h1>
    <div id="surveyContainer"></div>
    <button onclick="loadSurvey()">再生成</button> <!-- 質問を再生成するボタン -->
</body>
</html>
