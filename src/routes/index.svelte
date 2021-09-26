<script>
  import { Modals, closeModal, openModal } from 'svelte-modals'
  import { fade } from 'svelte/transition'

  import Start from '../components/_Start.svelte'
  import Icon from '../components/Icon.svelte'
  import Intro from '../components/Intro.svelte'
  import Button from '../components/Button.svelte'
  import Modal from '../components/Modal.svelte'
  
  let playerChoice = ''
  let houseChoice = ''
  let gameResult = ''
  
  let score = 0

  function handlePlayerSelect (choice) {
    const choices = ['paper', 'scissors', 'rock']
    playerChoice = choice

    setTimeout(() => {
      houseChoice = choices[Math.floor(Math.random() * 2)];

      gameResult = normalGame(playerChoice, houseChoice)
    }, 1000);
  }

  function normalGame (playerChoice, houseChoice){
    if (playerChoice === houseChoice) return 'draw'
    
    if (playerChoice === 'rock') {
      if (houseChoice === 'scissors') { 
        score++ 
        return 'you win'
      }
      if (houseChoice === 'paper') {
        score--
        return 'you lose'
      }
    }

    if (playerChoice === 'scissors') {
      if (houseChoice === 'paper') {
        score++ 
        return 'you win'
      }
      if (houseChoice === 'rock') {
        score--
        return 'you lose'
      }
    }

    if (playerChoice === 'paper') {
      if (houseChoice === 'rock') { 
        score++ 
        return 'you win'
      }
      if (houseChoice === 'scissors') { 
        score--
        return 'you lose'
      }
    }
  }

  function resetGame() {
    playerChoice = ''
    houseChoice = ''
    gameResult = ''
  }

  function handleClick() {
    openModal(Modal, { title: "Rules", rules: "normal" })
  }

</script>

<Start/>

<div class="game">
  <Intro {score}/>
  {#if playerChoice === ''}
    <div class="player-select">
      <Icon title="paper" on:click={() => handlePlayerSelect('paper')}/>
      <span/>
      <Icon title="scissors" on:click={() => handlePlayerSelect('scissors')}/>
      <span/>
      <span/>
      <span/>
      <span/>
      <Icon title="rock" on:click={() => handlePlayerSelect('rock')}/>
      <span/>
    </div>
  {:else}
    <div class="result">
      <div>
        <span>You picked</span>
        <Icon title={playerChoice}/>
      </div>
      <div class="">
        {#if houseChoice !== ''}
          <span class="game-result">{gameResult.toUpperCase()}</span>
          <Button big dense label="play again" on:click={resetGame}/>
        {/if}
      </div>
      <div>
        <span>The house picked</span>
        <Icon title={houseChoice}/>
      </div>
    </div>
  {/if}

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

  .player-select {
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

  .result {
    display: flex;
    justify-content: space-evenly;
    align-items: center;

    & > div {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    span {
      text-transform: uppercase;
      color: white;
      margin-bottom: 30px;
      &.game-result {
        margin-bottom: 10px;
        font-size: 2em;
      }
    }
  }
</style>