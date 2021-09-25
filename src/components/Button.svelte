<script>
import Icon from "./Icon.svelte";

  export let label = '';
  export let dense = false;
  export let big = false;
  export let full = false;
</script>

<button
  class:dense
  class:big
  class:full
  on:click
>
  {label.toUpperCase()}
</button>

<style lang="scss">
  button{

    background: transparent;
    border: 1px solid white;
    border-radius: 4px;
    padding: 0.75em 1.5em;
    color: white;
    letter-spacing: 2px;
    cursor: pointer;

    &.dense{
      background: white;
      color: hsl(229, 25%, 31%);
    }

    &.big{}

    &.full{
      width: 100%;
    }
  }
</style>