<script>
  import players from "./data/players";
  import Player from "./Player.svelte";
</script>

<style type="text/scss">
  @import url("https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,400;0,500;0,900;1,400&display=swap");
  @import "./theme.scss";
  :global(body, html) {
    margin: 0;
    padding: 0;
    position: relative;
    box-sizing: border-box;
    font-family: "Roboto", sans-serif;
    background: $background;
    color: $light-text;
  }
  :global(*, *:before, *:after) {
    box-sizing: inherit;
  }
  :global(h1, h2, h3, h4) {
    margin: 0;
    padding: 0;
  }
  .players {
    width: 100%;
    display: table;
    &__single {
      display: table-cell;
      width: 50%;
      padding-left: 10%;
      &:last-of-type {
        padding-left: 0;
        padding-right: 10%;
      }
    }
  }
  footer {
    margin: 50px 0 20px;
    &, a{
      color: $light-neutral;
      text-align: center;
      font-size: 11px;
    }
  }
  @media (max-width: 920px) {
    .players {
      &,
      &__single {
        display: block;
        width: 100%;
        &,
        &:last-of-type {
          padding: 0;
        }
      }
    }
  }
</style>

<main class="players">
  {#each players as player (player.id)}
    <div class="players__single">
      <Player {player} />
    </div>
  {/each}
</main>
<footer>
  <div>
    Icons made by
    <a href="https://www.flaticon.com/authors/freepik" title="Freepik">
      Freepik
    </a>
    from
    <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a>
  </div>
</footer>
