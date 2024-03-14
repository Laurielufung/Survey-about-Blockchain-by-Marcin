<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>nChain区块链讲座问卷调研</title>
    <style>
        /* CSS 样式 */
    </style>
</head>
<body>
    <div class="container" id="question1">
        <h2>探索数字世界：nChain区块链讲座问卷调研</h2>
        <p>嗨！亲爱的朋友，我们有幸邀请到 nChain 公司的总经理 Marcin Zarakowski于在4月24日专门从英国来深圳开办一场精彩的讲座！而这场讲座将以一种与众不同的方式呈现。在我们着手策划之前，我们想了解您对数字世界的想法，以及您对区块链技术和讲座形式的期待。请花几分钟时间填写这份有趣的问卷，帮助我们打造一个独具特色的讲座体验吧！</p>
        <button class="button" onclick="nextQuestion()">开始问卷</button>
    </div>

    <div class="container" id="question2" style="display: none;">
        <div class="question">
            <h3>如果数字世界是一部电影，您希望它的类型是什么？</h3>
            <input type="radio" name="question2" value="科幻冒险片"> 科幻冒险片：探索未知的数字星球<br>
            <input type="radio" name="question2" value="悬疑推理片"> 悬疑推理片：解开数字世界的神秘谜团<br>
            <input type="radio" name="question2" value="动画喜剧片"> 动画喜剧片：数字角色的欢乐冒险<br>
            <input type="radio" name="question2" value="古装偶像剧"> 古装偶像剧：了解数字世界的历史和发展<br>
            <input type="radio" name="question2" value="其他"> 其他：[填写您的选择]<br>
        </div>
        <button class="button" onclick="nextQuestion()">下一题</button>
    </div>

    <!-- 更多问题页面 -->

    <div class="container" id="qrCode" style="display: none;">
        <h3>请扫描以下二维码进入群组等待抽奖</h3>
        <img src="https://example.com/your-qr-code.png" alt="二维码">
    </div>

    <script>
        let surveyData = [];

        function collectData(question, answer) {
            surveyData.push({ question: question, answer: answer });
        }

        function nextQuestion() {
            // 获取问题和答案
            let question = document.getElementById('question' + currentQuestion).querySelector('.question').textContent.trim();
            let answer;
            if (document.querySelector('input[name="question' + currentQuestion + '"]:checked')) {
                answer = document.querySelector('input[name="question' + currentQuestion + '"]:checked').value;
            } else {
                answer = document.querySelector('input[name="question' + currentQuestion + '_other"]').value;
            }

            // 收集数据
            collectData(question, answer);

            // 显示下一题
            document.getElementById('question' + currentQuestion).style.display = 'none';
            currentQuestion++;
            if (currentQuestion <= 8) {
                document.getElementById('question' + currentQuestion).style.display = 'block';
            } else {
                document.getElementById('qrCode').style.display = 'block';
                // 导出数据
                exportData();
            }
        }

        function exportData() {
            let dataStr = JSON.stringify(surveyData);
            let dataUri = 'data:application/json;charset=utf-8,' + encodeURIComponent(dataStr);
            let exportLink = document.createElement('a');
            exportLink.setAttribute('href', dataUri);
            exportLink.setAttribute('download', 'survey_data.json');
            exportLink.click();
        }
    </script>
</body>
</html>
