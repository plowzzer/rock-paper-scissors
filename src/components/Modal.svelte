<script>
  import { closeModal } from 'svelte-modals'
	import { fly } from 'svelte/transition'
	
  export let isOpen
  export let title
  export let rules

  let normal = 'image-rules.svg'
  let bonus = 'image-rules-bonus.svg'
</script>

{#if isOpen}
  <div role="dialog" class="modal" transition:fly={{ y: 50 }} on:introstart on:outroend>
    <div class="contents">
      <h2>{title.toUpperCase()}</h2>
      {#if rules === 'normal'}
        <img src={normal} alt="Normal rules">
      {/if}
      {#if rules === 'spock-lizard'}
        <img src={bonus} alt="Bonus rules">
      {/if}
      <button on:click={closeModal} />
    </div>
  </div>
{/if}

<style lang="scss">
  .modal {
    position: fixed;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 999;
    pointer-events: none;
  }

  .contents {
    min-width: 100%;
    height: 100vh;
    padding: 100px 30px;
    background: white;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    pointer-events: auto;
  }

  h2 {
    text-align: center;
    font-size: 3em;
    color: hsl(229, 25%, 31%);
  }

  img {
    width: 75%;
    margin: auto;
  }

  button {
    position: relative;
    background: transparent;
    border: none;
    height: 30px;
    cursor: pointer;

    &:after,
    &:before {
      content: '';
      width: 4px;
      height: 30px;
      background: hsl(217, 16%, 45%);
      position: absolute;
      border-radius: 3px;

    }

    &:after{
      transform: rotate(45deg)
    }

    &:before{
      transform: rotate(-45deg)
    }

  }

</style>