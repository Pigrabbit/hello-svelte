<script>
  import AddPlayer from "./AddPlayer.svelte";
  import Navbar from "./Navbar.svelte";
  import Player from "./Player.svelte";

  let players = [
    {
      name: "Heungmin Son",
      points: 12,
    },
    {
      name: "Harry Kane",
      points: 15,
    },
    {
      name: "Gareth Bale",
      points: 5,
    },
  ];

  const addPlayer = (e) => {
    const newPlayer = e.detail;
    players = players.concat(newPlayer);
  };

  const removePlayer = (e) => {
    const playerToBeRemoved = e.detail;
    players = players.filter((player) => player.name !== playerToBeRemoved);
  };
</script>

<Navbar />
<div class="container">
  <AddPlayer on:addPlayer={addPlayer} />
  {#if players.length === 0}
    <p>No players available</p>
  {:else}
    {#each players as player}
      <Player
        name={player.name}
        points={player.points}
        on:removePlayer={removePlayer}
      />
    {/each}
  {/if}
</div>
