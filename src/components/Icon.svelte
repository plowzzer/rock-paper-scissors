<script>
  export let title
  export let gameResult
  export let big = false

  function translateImage (title) {
    return `./icon-${title}.svg`
  }
</script>

<div class={`${title} ${gameResult}`} class:big>
  {#if title}
    <button on:click>
      <img src={translateImage(title)} alt="{title}">
    </button>
  {/if}
</div>

<style lang="scss">
  div {
    height: 120px;
    width: 120px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 100%;
    background:hsla(237, 49%, 15%, 30%);
    position: relative;

    &.win {
      &::before{
        position: absolute;
        content: '';
        width: 120px;
        height: 120px;
        border-radius: 100%;
        z-index: 0;
        box-shadow: 0px 0px 160px white;
      }
    }

    &.paper{ 
      background-image: linear-gradient(hsl(230, 89%, 62%), hsl(230, 89%, 65%));
      box-shadow: inset 0px -8px 1px hsla(0,0%,0%,25%);
    }
    &.scissors{ 
      box-shadow: inset 0px -8px 1px hsla(0,0%,0%,25%);
      background-image: linear-gradient(hsl(39, 89%, 49%), hsl(40, 84%, 53%));
    }
    &.rock{ 
      box-shadow: inset 0px -8px 1px hsla(0,0%,0%,25%);
      background-image: linear-gradient(hsl(349, 71%, 52%), hsl(349, 70%, 56%));
    }

    &.lizard{
      box-shadow: inset 0px -8px 1px hsla(0,0%,0%,25%);
      background-image: linear-gradient(hsl(261, 73%, 60%), hsl(261, 72%, 63%));
    }

    &.spock{
      box-shadow: inset 0px -8px 1px hsla(0,0%,0%,25%);
      background-image: linear-gradient(hsl(189, 59%, 53%), hsl(189, 58%, 57%));
    }

    button {
      height: 90px;
      width: 90px;
      border-radius: 100%;
      border: none;
      box-shadow: inset 0px 6px 1px #ccc;
      cursor: pointer;
      z-index: 1;
    }

    @media (min-width: 640px) {
      height: 180px;
      width: 180px;
      button {
        height: 130px;
        width: 130px;
      }
      &.big {
        height: 240px;
        width: 240px;
        button {
          height: 170px;
          width: 170px;
        }
        &::before{
          height: 240px;
          width: 240px;
        }
      }
    }
  }
</style>