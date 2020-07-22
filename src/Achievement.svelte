<script>
  import { slide } from "svelte/transition";
  export let id, avatar, name, description, achieved;
  let visible = false;
  const state = achieved ? "achieved" : "pending";
  const avatarSrc = `./images/${state}/${avatar}.svg`;
  const toggleDec = () => (visible = !visible);
</script>

<style type="text/scss">
  @import "./theme.scss";
  .achievement {
    display: table;
    width: 100%;
    cursor: pointer;
    width: #{$avatar-width + 10px};
    margin: 30px 0 #{$achievement-width - 20px} 0;
    text-align: center;
    background: $light-text;
    color: $dark-text;
    padding: 10px;
    border-radius: 10px;
    position: relative;
    left: calc(50% - #{$avatar-width / 2 - 10px});
    font-size: 14px;
    &__img {
      left: calc(-1 * #{$achievement-width / 2});
      top: #{-1 * $achievement-width / 2 + 20px};
      position: absolute;
      vertical-align: middle;
      width: $achievement-width;
      height: $achievement-width;
      padding: 10px;
      background: $light-neutral;
      border-radius: #{$achievement-width + 10px};
      margin: 0;
      img {
        display: block;
      }
    }
    &__details {
      vertical-align: middle;
    }
    &__caption {
      display: inline-block;
      font-weight: 900;
      color: $light-coloured;
      font-size: 16px;
    }
    &__description {
      overflow: hidden;
      padding: 10px 10px 10px 30px;
    }
  }
</style>

<article
  class={`achievement achievement--id-${id} achievement--${state}`}
  on:click={toggleDec}>
  <figure class="achievement__img">
    <img src={avatarSrc} alt="" />
  </figure>
  <div class="achievement__details">
    <div class="achievement__caption">{name}</div>
    {#if visible}
      <div class="achievement__description" transition:slide>{description}</div>
    {/if}
  </div>
</article>
