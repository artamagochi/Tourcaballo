# Tourcaballo
<script>

var N=8
var gfg = new Array(N);
// Loop to create 2D array using 1D array

for (var i = 0; i < gfg.length; i++) 
{
  gfg[i] = new Array(N);
}

// Loop to initilize 2D array elements.

for (var i = 0; i < N; i++) {

  for (var j = 0; j < N; j++) {

    gfg[i][j] = -1;

  }

}
function displaySolution(gfg) {

  for (var i = 0; i < N; i++) {

    for (var j = 0; j < N; j++)    {

      document.write(gfg[i][j] + " ");

    }

    document.write("<br>");

  } 

}

function check ( x, y, matriz)

{

  if (x<0) return -1;

  if(y<0) return -1;

  if(x>=N) return -1;

  if(y>= N) return -1;

  if(matriz[x][y]==-1) return 1;

}
displaySolution(gfg);

function  knightTour(x, y, move, sol , xMove, yMove) {

  var xNext, yNext;

  if (move == N*N)     //when the total board is covered

  return true;
 

  for (var k = 0; k < N; k++) {

    xNext = x + xMove[k];

    yNext = y + yMove[k];

    if (check(xNext, yNext, sol)==1)  {   //check room is preoccupied or not

      sol[xNext][yNext] = move;

      if (knightTour(xNext, yNext, move+1, sol, xMove, yMove) == true)

        return true;

      else

        sol[xNext][yNext] = -1;// backtracking

    }

  }

  return false;

}

function findKnightTourSol() {
var N=8
var sol = new Array(N);
// Loop to create 2D array using 1D array

for (var i = 0; i < gfg.length; i++) 
{
  sol[i] = new Array(N);
}

// Loop to initilize 2D array elements.

for (var i = 0; i < N; i++) {

  for (var j = 0; j < N; j++) {

    sol[i][j] = -1;

  }

}
  

  //all possible moves for knight

  var xMove = [ 2, 1, -1, -2, -2, -1,  1,  2 ];

  var yMove = [ 1, 2,  2,  1, -1, -2, -2, -1 ];

  sol[0][0]  = 0;     //starting from room (0, 0)

 

  if (knightTour(0, 0, 1, sol, xMove, yMove) == false) {

    cout << "Solution does not exist";

    return false;

  } else

    displaySolution(sol);

  return true;

}

findKnightTourSol();

</script>

