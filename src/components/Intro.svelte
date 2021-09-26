<script>
  export let score
</script>

<header>
  <h1 class="title">
    <span>Rock</span>
    <span>Paper</span>
    <span>Scissors</span>
  </h1>

  <div class="score">
    <span>score</span>
    <h2>{score}</h2>
  </div>
</header>

<style lang="scss">
  header{
    border: 2px solid hsl(217, 16%, 45%);
    border-radius: 10px;
    padding: 1em 0.7em;
    display: flex;
    justify-content: space-between;
    width: 100%;
    max-width: 600px;
    margin: 0 auto;
    height: 160px;
    align-items: center;
  }

  h1 {
    text-transform: uppercase;
    color:white;
    display: flex;
    flex-direction: column;
  }

  .score{
    background: white;
    border-radius: 6px;
    width: 120px;
    height: 130px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
   
    span {
      color: hsl(229, 64%, 46%);
      letter-spacing: 3px;
      text-transform: uppercase;
    }
    
    h2 {
      font-size: 3em;
      color: hsl(229, 25%, 31%);
    }
  }
</style>