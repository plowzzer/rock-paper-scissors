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
  let gameResultInvert = ''
  let humanizeGameResult = ''
  
  let score = 0

  function handlePlayerSelect (choice) {
    const choices = ['paper', 'scissors', 'rock']
    playerChoice = choice

    setTimeout(() => {
      houseChoice = choices[Math.floor(Math.random() * 2)];

      gameResult = normalGame(playerChoice, houseChoice)
      gameResultInvert = invertResult(gameResult)
    }, 1000);
  }

  function normalGame (playerChoice, houseChoice){
    if (playerChoice === houseChoice) return 'draw'
    
    if (playerChoice === 'rock') {
      if (houseChoice === 'scissors') { 
        score++ 
        return 'win'
      }
      if (houseChoice === 'paper') {
        score--
        return 'lose'
      }
    }

    if (playerChoice === 'scissors') {
      if (houseChoice === 'paper') {
        score++ 
        return 'win'
      }
      if (houseChoice === 'rock') {
        score--
        return 'lose'
      }
    }

    if (playerChoice === 'paper') {
      if (houseChoice === 'rock') { 
        score++ 
        return 'win'
      }
      if (houseChoice === 'scissors') { 
        score--
        return 'lose'
      }
    }
  }

  function invertResult (gameResult){
    if(gameResult !== '' && gameResult !== 'draw') {
      return gameResult === 'win' ? 'lose' : 'win'
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
  <div class="container">
    <div class="grid">
      <Intro {score}/>
      {#if playerChoice === ''}
        <div class="player-select">
          <div class="w-1-2">
            <Icon title="paper" on:click={() => handlePlayerSelect('paper')}/>
          </div>
          <div class="w-1-2">
            <Icon title="scissors" on:click={() => handlePlayerSelect('scissors')}/>
          </div>
          <div class="w-1-1">
            <Icon title="rock" on:click={() => handlePlayerSelect('rock')}/>
          </div>
        </div>
      {:else}
        <div class="result">
          <div>
            <span>You picked</span>
            <Icon big title={playerChoice} {gameResult} />
          </div>
          <div class="">
            {#if houseChoice !== ''}
              <span class="game-result">{gameResult.toUpperCase()}</span>
              <Button big dense label="play again" on:click={resetGame}/>
            {/if}
          </div>
          <div>
            <span>The house picked</span>
            <Icon big title={houseChoice} gameResult={gameResultInvert}/>
          </div>
        </div>
      {/if}
    
      <footer>
        <Button label="rules" on:click={handleClick}/>
      </footer>
    </div>
  </div>
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
    background: radial-gradient(hsl(214, 47%, 23%), hsl(237, 49%, 15%));
    display: flex;
    flex-direction: column;
  }

  .player-select {
    position: relative;
    padding: 20px 0px 0px;
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    text-align: center;
    
    @media (min-width: 640px) {
      padding: 80px 70px 40px;
    }

    .w-1-1,
    .w-1-2 {
      padding-bottom:30px;
      display: flex;
      justify-content: center;
    }
  }

  .result {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;

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