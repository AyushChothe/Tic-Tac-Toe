<script>
  let grid = ["", "", "", "", "", "", "", "", ""];
  let player = "X";
  function setPalyer(i) {
    if (grid[i] == "") {
      grid[i] = player;
      player = player == "X" ? "O" : "X";
      setTimeout(() => {
        check();
      }, 1);
    }
  }

  function check() {
    const winning = [
      [0, 1, 2],
      [3, 4, 5],
      [6, 7, 8],
      [0, 3, 6],
      [1, 4, 7],
      [2, 5, 8],
      [0, 4, 8],
      [2, 4, 6]
    ];

    winning.forEach(cond => {
      if (
        grid[cond[0]] == grid[cond[1]] &&
        grid[cond[1]] == grid[cond[2]] &&
        grid[cond[0]] != ""
      ) {
        player = "";
        alert(grid[cond[0]] + " is Winner!");
        grid = ["", "", "", "", "", "", "", "", ""];
        player = "X";
      }
    });
  }
</script>

<style>
  main {
    text-align: center;
    padding: 1em;
    height: 80%;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
  }

  h1 {
    color: #ff3e00;
    text-transform: capitalize;
    font-size: 4em;
    font-weight: 100;
    width: 100%;
  }

  p {
    text-align: center;
    font-size: 1.5rem;
  }

  .grid {
    width: 18rem;
    height: 18rem;
    display: flex;
    flex-wrap: wrap;
  }

  .square {
    background-color: pink;
    width: 5rem;
    height: 5rem;
    margin: 5px;
  }
</style>

<main>
  <div>
    <h1>{player} Turn</h1>

    <div class="grid">
      {#each grid as item, i}
        <div
          class="square"
          on:click={() => {
            setPalyer(i);
          }}>
          <p>{item}</p>
          <p />
        </div>
      {/each}
    </div>
  </div>
</main>
