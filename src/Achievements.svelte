<script>
  import Achievement from "./Achievement.svelte";
  import achievementsList from "./data/achievements";
  export let achievements;
</script>

<section>
  {#each achievementsList as achievementSingle (achievementSingle.id)}
    <Achievement {...achievementSingle} achieved={achievements.indexOf(achievementSingle.id)!==-1}/>
  {/each}
</section>
