<script>
  export let title

  function translateImage (title) {
    return `./icon-${title}.svg`
  }
</script>

<div class="{title}">
  <button>
    <img src={translateImage(title)} alt="{title}">
  </button>
</div>

<style lang="scss">
  div {
    height: 180px;
    width: 180px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 100%;
    box-shadow: inset 0px -8px 1px hsla(0,0%,0%,25%);
    
    &.paper{ background-image: linear-gradient(hsl(230, 89%, 62%), hsl(230, 89%, 65%)); }
    &.scissors{ background-image: linear-gradient(hsl(39, 89%, 49%), hsl(40, 84%, 53%)); }
    &.rock{ background-image: linear-gradient(hsl(349, 71%, 52%), hsl(349, 70%, 56%)); }

    button {
      height: 130px;
      width: 130px;
      border-radius: 100%;
      border: none;
      box-shadow: inset 0px 6px 1px #ccc;
      cursor: pointer;
    }
  }
</style>