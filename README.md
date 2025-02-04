<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tic Tac Toe</title>
    <style>
        table { border-collapse: collapse; margin: 20px auto; }
        td { width: 60px; height: 60px; text-align: center; font-size: 24px; border: 2px solid black; cursor: pointer; }
    </style>
</head>
<body>
    <h1>Tic-Tac-Toe</h1>
    <table>
        <tr>
            <td onclick="makeMove(this, 0)"></td>
            <td onclick="makeMove(this, 1)"></td>
            <td onclick="makeMove(this, 2)"></td>
        </tr>
        <tr>
            <td onclick="makeMove(this, 3)"></td>
            <td onclick="makeMove(this, 4)"></td>
            <td onclick="makeMove(this, 5)"></td>
        </tr>
        <tr>
            <td onclick="makeMove(this, 6)"></td>
            <td onclick="makeMove(this, 7)"></td>
            <td onclick="makeMove(this, 8)"></td>
        </tr>
    </table>
    <p id="winner"></p>

    <script>
        let board = ["", "", "", "", "", "", "", "", ""];
        let currentPlayer = "X";

        function makeMove(cell, index) {
            if (board[index] === "" && document.getElementById("winner").innerText === "") {
                board[index] = currentPlayer;
                cell.innerText = currentPlayer;
                if (checkWinner()) {
                    document.getElementById("winner").innerText = currentPlayer + " wins!";
                } else {
                    currentPlayer = currentPlayer === "X" ? "O" : "X";
                }
            }
        }

        function checkWinner() {
            let winPatterns = [
                [0, 1, 2], [3, 4, 5], [6, 7, 8], 
                [0, 3, 6], [1, 4, 7], [2, 5, 8], 
                [0, 4, 8], [2, 4, 6]
            ];
            return winPatterns.some(pattern => 
                board[pattern[0]] !== "" && 
                board[pattern[0]] === board[pattern[1]] && 
                board[pattern[1]] === board[pattern[2]]
            );
        }
    </script>
</body>
</html>
