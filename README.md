/*  # Tic_Tac_Toe
A Famous Game (C++) **/

#include <iostream> 
#include <vector>

using namespace std;

// Function to draw the Tic Tac Toe board
void drawBoard(const vector<char>& board) {
    cout << "-------------" << endl;
    cout << "| " << board[0] << " | " << board[1] << " | " << board[2] << " |" << endl;
    cout << "-------------" << endl;
    cout << "| " << board[3] << " | " << board[4] << " | " << board[5] << " |" << endl;
    cout << "-------------" << endl;
    cout << "| " << board[6] << " | " << board[7] << " | " << board[8] << " |" << endl;
    cout << "-------------" << endl;
}

// Function to check if any player has won
bool checkWin(const vector<char>& board, char player) {
    // Check rows
    if ((board[0] == player && board[1] == player && board[2] == player) ||
        (board[3] == player && board[4] == player && board[5] == player) ||
        (board[6] == player && board[7] == player && board[8] == player)) {
        return true;
    }
    
    // Check columns
    if ((board[0] == player && board[3] == player && board[6] == player) ||
        (board[1] == player && board[4] == player && board[7] == player) ||
        (board[2] == player && board[5] == player && board[8] == player)) {
        return true;
    }
    
    // Check diagonals
    if ((board[0] == player && board[4] == player && board[8] == player) ||
        (board[2] == player && board[4] == player && board[6] == player)) {
        return true;
    }
    
    return false;
}

// Function to check if the game is a draw
bool checkDraw(const vector<char>& board) {
    for (char cell : board) {
        if (cell == ' ')
            return false;
    }
    return true;
}

int main() {
    vector<char> board(9, ' ');
    char currentPlayer = 'X';
    int move;
    
    cout << "Tic Tac Toe Game" << endl;
    cout << "Player 1: X | Player 2: O" << endl;
    
    while (true) {
        drawBoard(board);
        
        // Get current player's move
        cout << "Player " << currentPlayer << "'s turn. Enter your move (1-9): ";
        cin >> move;
        move--;  // Convert move to 0-based index
        
        // Check if move is valid
        if (move < 0 || move >= 9 || board[move] != ' ') {
            cout << "Invalid move! Try again." << endl;
            continue;
        }
        
        // Update the board
        board[move] = currentPlayer;
        
        // Check if the current player has won
        if (checkWin(board, currentPlayer)) {
            drawBoard(board);
            cout << "Player " << currentPlayer << " wins!" << endl;
            break;
        }
        
        // Check if the game is a draw
        if (checkDraw(board)) {
            drawBoard(board);
            cout << "The game is a draw." << endl;
            break;
        }
        
        // Switch to the other player
        currentPlayer = (currentPlayer == 'X') ? 'O' : 'X';
    }
    
    return 0;
}



