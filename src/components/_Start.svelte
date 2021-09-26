<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Barlow+Semi+Condensed:wght@600;700&display=swap');

:global(*) {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Barlow Semi Condensed', sans-serif;
}

:global(.container) {
  display: flex;
  position: relative;
  box-sizing: border-box;
  max-width: 1000px;
  height: 100%;
  width: 100%;
  margin-left: auto;
  margin-right: auto;
  padding-left: 15px;
  padding-right: 15px;
  @media (min-width: 640px) {
    padding-left: 30px;
    padding-right: 30px;
  }
  @media (min-width: 960px) {
    padding-left: 40px;
    padding-right: 40px;
  }
}

:global(.grid) {
  padding-top: 30px;
  padding-bottom: 30px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 100%;
}

:global(.w-1-1) {
  width: 100%;
}

:global(.w-1-2) {
  width: 50%;
}
</style>