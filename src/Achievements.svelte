<script>
  import { slide } from "svelte/transition";
  import Achievement from "./Achievement.svelte";
  import achievementsList from "./data/achievements";
  export let achievements, singleLevel, visible;
  let isVisible = visible;
  const isAchieved = (level, id) => {
    return achievements[`level${level}`].indexOf(id) !== -1;
  };
  const toggleDec = () => {
    return (isVisible = !isVisible);
  };
</script>

<section>
  <div class="title" on:click={toggleDec}>
    <h1>Level {singleLevel}:</h1>
  </div>
  {#if isVisible}
    <div transition:slide>
      {#each achievementsList as achievementSingle (achievementSingle.id)}
        <Achievement
          {...achievementSingle}
          achieved={isAchieved(singleLevel, achievementSingle.id)}
          level={singleLevel}
        />
      {/each}
    </div>
  {/if}
</section>

<style type="text/scss">
  @import "./theme.scss";
  div.title {
    text-align: center;
    cursor: pointer;
  }
  h1 {
    text-align: center;
    margin: 10px auto;
    line-height: 30px;
    display: inline-block;
    vertical-align: middle;
    background-color: $dark-text;
    border-radius: 15px;
    width: 50%;
    &:hover {
      background-color: $light-neutral;
    }
  }
</style>
