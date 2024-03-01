<h1> Tic Tac Toe game with Golang </h1>
<h4>Since i am learning Golang, this is my first project, tic tac toe that runs in the command line. <br>
Known bug: It prints x as the winner even if o wins. Please help with the fix</h4>

<h2>Credits</h2>
https://github.com/sts10/tic-tac-go <br>
https://github.com/sts10 <br>
https://tour.golang.org/list 



<br>

# Building a Tic Tac Toe Game in Go

## Intro

Tic Tac Toe is a classic game that challenges players to strategically place their marks on a 3x3 grid, with the goal of getting three of their marks in a row, either horizontally, vertically, or diagonally. In this article, we will explore how to build a simple Tic Tac Toe game using the Go programming language. We will go through the code step by step, explaining its purpose and functionality.

## Setting up the Game

The first step in building our Tic Tac Toe game is to set up the necessary structures and variables. We define a `Game` struct that represents the state of the game. It consists of a `board` array, which stores the positions of the marks, the current `player`, and the `turnNumber` to keep track of the number of moves.

```go
type Game struct {
    board      [9]string
    player     string
    turnNumber int
}

func main() {
    var game Game
    game.player = "O"
    // ...
}
```

## Game Logic

Next, we implement the game logic within a loop that continues until the game is over. Inside the loop, we print the current state of the board, ask the player for their move, and then attempt to make the move.

```go
for gameOver != true {
    PrintBoard(game.board)
    move := askforplay()
    err := game.play(move)
    if err != nil {
        fmt.Println(err)
        continue
    }

    gameOver, winner = CheckForWinner(game.board, game.turnNumber)
}
```

### Making a Move

The `play` method of the `Game` struct handles the player's move. It checks if the selected position is available on the board and updates the board accordingly. It also switches the current player and increments the turn number.

```go
func (game *Game) play(pos int) error {
    if game.board[pos-1] == "" {
        game.board[pos-1] = game.player
        game.SwitchPlayers()
        game.turnNumber += 1
        return nil
    }
    return errors.New("try another move")
}
```

### Checking for a Winner

We use the `CheckForWinner` function to determine if there is a winner or if the game is a draw. This function checks for winning combinations horizontally, vertically, and diagonally. If a winning combination is found, the function returns `true` along with the winning player's mark.

```go
func CheckForWinner(b [9]string, n int) (bool, string) {
    // ...
}
```

## User Interaction

To make the game more interactive, we provide a way for the players to input their moves. The `askforplay` function prompts the player to enter a position, and the input is then returned as an integer.

```go
func askforplay() int {
    var moveInt int
    fmt.Println("Enter Pos to play: ")
    fmt.Scan(&moveInt)
    return moveInt
}
```

## Displaying the Board

The `PrintBoard` function is responsible for displaying the current state of the board. It clears the screen, iterates over the board array, and prints out the marks in a 3x3 grid format.

```go
func PrintBoard(b [9]string) {
    ClearScreen()
    for i, v := range b {
        // ...
    }
}
```

## Conclusion

In this article, we have walked through the process of building a simple Tic Tac Toe game in the Go programming language. We covered the setup of the game, the game logic, user interaction, and displaying the board. By understanding this code, you now have a foundation to build upon and expand the game further. Have fun exploring different strategies and enhancing the game with additional features!

Remember, programming is problen solving and a creative process, and there are endless possibilities for customization and improvement. So go ahead and challenge yourself to make the game even more exciting and engaging.
