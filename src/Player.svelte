<script>
  import Achievements from "./Achievements.svelte";
  export let player;
  const { name, surname, avatar, achievements, level } = player;
</script>

<style type="text/scss">
  @import "./theme.scss";
  h2 {
    font-size: 40px;
    font-weight: 900;
    text-align: center;
    color: $light-text;
  }
  h3 {
    font-weight: 500;
    text-align: center;
  }
  img {
    margin: 70px auto 10px auto;
    width: $avatar-width;
    display: block;
    border-radius: #{$avatar-width / 2};
  }
  figure {
    position: relative;
    &:after {
      content: "";
      display: block;
      position: absolute;
      top: 0;
      bottom: 0;
      left: 0;
      right: 0;
      border-radius: #{$avatar-width / 2 + 10px};
      border: 10px solid $light-neutral;
      width: #{$avatar-width + 18px};
      height: #{$avatar-width + 18px};
      margin: auto;

    }
  }
</style>

<section>
  <header>
    <figure>
      <img src={`./images/${avatar}`} alt={`${name} ${surname}`} />
    </figure>
    <h2>{name}</h2>
    <!-- <h3>Level {level[level.length-1]}</h3> -->
  </header>
  {#each level as singleLevel, i}
    <Achievements {achievements} {singleLevel} visible={i == level.length-1}/>
  {/each}
</section>
