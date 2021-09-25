<script>
  import { Modals, closeModal, openModal } from 'svelte-modals'
  import { fade } from 'svelte/transition'

  import Icon from '../components/Icon.svelte'
  import Intro from '../components/Intro.svelte'
  import Button from '../components/Button.svelte'
  import Modal from '../components/Modal.svelte'

  function handleClick() {
    openModal(Modal, { title: "Rules", rules: "normal" })
  }
</script>

<div class="game">
  <Intro score="0"/>

  <div class="selection-grid">
    <Icon title="paper"/>
    <span/>
    <Icon title="scissors"/>
    <span/>
    <span/>
    <span/>
    <span/>
    <Icon title="rock"/>
    <span/>
  </div>

  <footer>
    <Button label="rules" on:click={handleClick}/>
  </footer>

  
</div>

<Modals>
  <div
    slot="backdrop"
    class="backdrop"
    transition:fade
    on:click={closeModal}
  />
</Modals>

<style lang='scss'>
  @import url('https://fonts.googleapis.com/css2?family=Barlow+Semi+Condensed:wght@600;700&display=swap');

  :global(*) {
		margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Barlow Semi Condensed', sans-serif;
	}

  .backdrop {
    position: fixed;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    background: rgba(0,0,0,0.50)
  }

  .game {
    width: 100%;
    height: 100vh;
    margin: 0;
    padding: 0;
    background: radial-gradient(hsl(214, 47%, 23%), hsl(237, 49%, 15%));
    padding: 30px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .selection-grid {
    position: relative;
    padding: 50px;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows:repeat(3, 1fr);
    justify-items: center;
    justify-content: center;

    &:after{
      content: '';
      background: url('bg-triangle.svg');
      background-color: red;
      width: 100%;
      height: 100%;
    }
  }
</style>