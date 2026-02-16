<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>26週後カレンダー計算</title>

<style>
body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  text-align: center;
  padding: 40px;
  background-color: #f4f6f8;
}

.container {
  background: white;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  max-width: 400px;
  margin: auto;
}

h1 {
  font-size: 22px;
}

.result {
  margin-top: 20px;
  font-size: 20px;
  font-weight: bold;
  color: #007aff;
}
</style>
</head>

<body>

<div class="container">
  <h1>26週後の日付を計算</h1>

  <input type="date" id="startDate">

  <div class="result" id="result"></div>
</div>

<script>
const startInput = document.getElementById("startDate");
const resultDiv = document.getElementById("result");

// 今日の日付を自動セット
const today = new Date();
startInput.valueAsDate = today;

// 計算処理
function calculate() {
  const startDate = new Date(startInput.value);
  if (!startDate) return;

  const futureDate = new Date(startDate);
  futureDate.setDate(futureDate.getDate() + (26 * 7));

  const options = { 
    year: 'numeric', 
    month: 'long', 
    day: 'numeric',
    weekday: 'long'
  };

  resultDiv.textContent = "26週後 → " + 
    futureDate.toLocaleDateString('ja-JP', options);
}

// 初回実行
calculate();

// 入力変更時に再計算
startInput.addEventListener("change", calculate);
</script>

</body>
</html>