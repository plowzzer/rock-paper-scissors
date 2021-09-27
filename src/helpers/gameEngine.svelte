<script context="module">
  export function normalGame (playerChoice, houseChoice){
    if (playerChoice === houseChoice) return 'draw'
    
    if (playerChoice === 'rock') {
      if (houseChoice === 'scissors') return 'win'
      if (houseChoice === 'paper') return 'lose'
    }

    if (playerChoice === 'scissors') {
      if (houseChoice === 'paper') return 'win'
      if (houseChoice === 'rock') return 'lose'
    }

    if (playerChoice === 'paper') {
      if (houseChoice === 'rock') return 'win'
      if (houseChoice === 'scissors') return 'lose'
    }
  }

  export function lizardSpockGame (playerChoice, houseChoice) {
    console.log(playerChoice, houseChoice)
    if (playerChoice === houseChoice) {
      console.log('draw')
      return 'draw'
    }

    if (playerChoice === 'scissors') {
      if (houseChoice === 'paper' || houseChoice === 'lizard') return 'win'
      if (houseChoice === 'rock' || houseChoice === 'spock') return 'lose'
    }

    if (playerChoice === 'paper') {
      if (houseChoice === 'rock' || houseChoice === 'spock') return 'win'
      if (houseChoice === 'lizard' || houseChoice === 'scissors') return 'lose'
    }

    if (playerChoice === 'rock') {
      if (houseChoice === 'lizard' || houseChoice === 'scissors') return 'win'
      if (houseChoice === 'spock' || houseChoice === 'paper') return 'lose'
    }

    if (playerChoice === 'lizard') {
      if (houseChoice === 'spock' || houseChoice === 'paper') return 'win'
      if (houseChoice === 'rock' || houseChoice === 'scissors') return 'lose'
    }

    if (playerChoice === 'spock') {
      if (houseChoice === 'scissors' || houseChoice === 'rock') return 'win'
      if (houseChoice === 'paper' || houseChoice === 'lizard') return 'lose'
    }
  }
</script>