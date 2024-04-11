# chess-cpp
A chess program written in C++

## Design
`Position`
- `pair<int, int> move`: the best/refutation move
- `int depth`: the depth that the position was considered
- `int nodeType`: the type of the node
  - 0b00: Exact value
  - 0b01: Lower bound
  - 0b10: Upper bound
- `double score`: the score for the best/refutation move
- `int age`: the age of the position, if the age is greater than a certain constant, the position will be replaced

`Game`
- `pair<int, int> prevMove`: stores the previous position of the piece that just moved and the current position of the piece that just moved
- `string fen()`: finds the fen string representation of the current position of the board
- `int enPassantTarget`: stores a position which is a target for en passant
- `int fullMoveClock`: stores the number of full moves played
- `int halfMoveClock`: stores the number of half moves played since the last piece capture or pawn push
- `bool inCheck(vector<int> position, bool whiteKing)`: checks if the white/black king is in check
- `double eval()`: the evaluation of the position
- `vector<pair<int, int>> childrenPositions(position position)`: finds all children positions of the inputted position and sorts them in order of best to worst.
- `double miniMax(vector<int> position, bool whiteMove, double alpha, double beta)`: the minimax evaluation
- `unordered_map<int, Position> positionCache`: stores the previously calculated positions

