<!DOCTYPE html>
<html>
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
      <title>井字遊戲</title>

      <style>
          * {
              font-family: Arial;
          }

          header, footer {
              background-color: #555555;
              color: #f0f0f0;
              text-align: center;
              padding: 10px;
          }

          main {
              padding: 10px 0;
          }

          .grid-container {
              display: grid;
              grid-template-columns: repeat(3, 1fr);
              grid-gap: 10px;
              width: 240px;
              margin: auto;
          }

          .grid-item {
              display: grid;
              width: 80px;
              height: 80px;
              justify-content: center;
              align-items: center;
              background-color: #F0F0F0;
              cursor: pointer;
          }
      </style>
  </head>

  <body>

  <header>
      <h1>井字遊戲</h1> <!-- 頁面標題 -->
  </header>
    <div class="grid-container">
  <style>
    .board {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 5px;
      margin: auto;
      width: 250px;
      height: 250px;
    }
    .cell {
      display: grid;
      width: 80px;
      height: 80px;
      justify-content: center;
      align-items: center;
      background-color: #F0F0F0;
      cursor: pointer; 
    }
  </style>
</head>

  <div class="board">
    <div class="cell" onclick="board(0)"></div>
    <div class="cell" onclick="board(1)"></div>
    <div class="cell" onclick="board(2)"></div>
    <div class="cell" onclick="board(3)"></div>
    <div class="cell" onclick="board(4)"></div>
    <div class="cell" onclick="board(5)"></div>
    <div class="cell" onclick="board(6)"></div>
    <div class="cell" onclick="board(7)"></div>
    <div class="cell" onclick="board(8)"></div>
  </div><!-- 上面的數字有9個，由左上的0，到右下的8，是顯示X和O在格上點擊後，就會固定而不變 -->
      
  <script>
    let currentPlayer = "X";
    let cells = document.querySelectorAll(".cell");
    let gameFinished = false;/* let 是用於 */
    
    function board(index) {
      if (cells[index].innerHTML === "" && !gameFinished) {
        cells[index].innerHTML = currentPlayer;
        checkWinner();
        currentPlayer = currentPlayer === "X" ? "O" : "X";}}

    function checkWinner() {
    const winningCombos = [
      [0, 1, 2],
      [3, 4, 5],
      [6, 7, 8],
      [0, 3, 6],
      [1, 4, 7],
      [2, 5, 8],
      [0, 4, 8],
      [2, 4, 6]
    ];/* 3個數字共9排，有打橫、打直和打斜，如[0, 1, 2]是最上面的3個網格（即打橫），[0, 3, 6]是最左側面的3個網格（即打直），[0, 4, 8]是從左上的網格（0），經過中間的網格（4），往右下打斜到右下的網格（8），這是一個矩陣，這數字是為了令其中一方的玩家在過關後顯示誰勝誰負 */
      /* 利用 const 為了令X和O的兩個玩家在網格在點擊後固定不變 */
      for (let combo of winningCombos) {
        const [a, b, c] = combo;
        if (
          cells[a].innerHTML &&
          cells[a].innerHTML === cells[b].innerHTML &&
          cells[a].innerHTML === cells[c].innerHTML
        ) {
          alert(currentPlayer + "勝出!");
          winner = true;
          return;
        }
      }

      if ([...cells].every(cell => cell.innerHTML !== "")) {
        alert("平局!");
        winner = true;
      }
    }
  </script>
</body>
</html>

</body>
</html>
