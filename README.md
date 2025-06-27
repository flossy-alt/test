```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Tic Tac Toe</title>
  <style>
    body { font-family: sans-serif; display: flex; justify-content: center; align-items: center; height: 100vh; background: #f0f0f0; }
    .board { display: grid; grid-template-columns: repeat(3, 100px); grid-gap: 5px; }
    .cell {
      width: 100px; height: 100px;
      background: white; display: flex;
      justify-content: center; align-items: center;
      font-size: 2.5em; cursor: pointer;
      border: 2px solid #333;
    }
    .status { margin-top: 20px; font-size: 1.2em; text-align: center; }
  </style>
</head>
<body>

<div>
  <div class="board" id="board"></div>
  <div class="status" id="status">Current: X</div>
</div>

<script>
  const board = document.getElementById('board');
  const status = document.getElementById('status');
  let currentPlayer = 'X';
  let cells = Array(9).fill(null);

  function checkWinner() {
    const wins = [
      [0,1,2], [3,4,5], [6,7,8],
      [0,3,6], [1,4,7], [2,5,8],
      [0,4,8], [2,4,6]
    ];
    for (let combo of wins) {
      const [a, b, c] = combo;                                                                                                                                     if (cells[a] && cells[a] === cells[b] && cells[a] === cells[c]) {
        return cells[a];
      }
    }
    return cells.includes(null) ? null : 'Draw';
  }

  function handleClick(i) {
    if (cells[i] || checkWinner()) return;
    cells[i] = currentPlayer;
    render();
    const winner = checkWinner();
    if (winner) {
      status.textContent = winner === 'Draw' ? 'Game Draw!' : `winner Wins¡;
     else 
      currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
      status.textContent = Current:{currentPlayer};
    }
  }

  function render() {
    board.innerHTML = '';
    cells.forEach((cell, i) => {
      const div = document.createElement('div');
      div.className = 'cell';
      div.textContent = cell || '';
      div.onclick = () => handleClick(i);
      board.appendChild(div);
    });
  }

  render();
</script>

</body>
</html>
```

---

You can open this file in any browser — works offline too. Want a version with reset or multiplayer features?
