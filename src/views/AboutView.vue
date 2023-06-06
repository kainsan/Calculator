<template>
  <div class="wrapper">
    <section class="screen">
      0
    </section>

    <section class="calc-btns">
      <div class="calc-btn-row">
        <button class="calc-btn double">C</button>
        <button class="calc-btn">&larr;</button>
        <button class="calc-btn">&divide;</button>
      </div>

      <div class="calc-btn-row">
        <button class="calc-btn">7</button>
        <button class="calc-btn">8</button>
        <button class="calc-btn">9</button>
        <button class="calc-btn">&times;</button>
      </div>

      <div class="calc-btn-row">
        <button class="calc-btn">4</button>
        <button class="calc-btn">5</button>
        <button class="calc-btn">6</button>
        <button class="calc-btn">&minus;</button>
      </div>

      <div class="calc-btn-row">
        <button class="calc-btn">1</button>
        <button class="calc-btn">2</button>
        <button class="calc-btn">3</button>
        <button class="calc-btn">&plus;</button>
      </div>
      <div class="calc-btn-row">
        <button class="calc-btn triple">0</button>
        <button class="calc-btn triple">&equals;</button>
      </div>
    </section>
  </div>
</template>

<style>
html{
  box-sizing: border-box ;
  height: 100%; 
}
*,
*::before,
*::after{
    box-sizing: inherit;
    margin: 0;
    padding: 0;
}
body{
    align-items: center;
    background: linear-gradient(320deg,#3a0f80,#490941);
    display: flex;
    font-family: 'Dosis', sans-serif;
    font-display: swap;
    height: inherit;
    justify-content: center;
}
.wrapper{
  backdrop-filter: blur(5.5px);
  -webkit-backdrop-filter: blur(5.5px);
  border-radius: 16px;
  box-shadow: 0 4px 30px rgba(35, 35, 35, 0.1);
  color: black;
  backdrop-filter: blur(4px);
  -webkit-backdrop-filter: blur(4px);
  background: rgba(255, 255, 255, 0.3);
  border: 1px solid rgba(255, 255, 255, 0.34);
  flex-basis: 400px;
  height: 540px;
  padding: 20px 35px;
}

.screen{
  backdrop-filter: blur(5.5px);
  -webkit-backdrop-filter: blur(5.5px);
  background: rgba(255, 255, 255, 0.75);
  border: 1px solid rgba(255, 255, 255, 0.01);
  border-radius: 16px;
  box-shadow: 0 4px 30px rgba(35, 35, 35, 0.1);
  color: black;
  font-size: 35px;
  overflow: auto;
  padding: 20px;
  text-align: right;
  width: 326px; 
}
.calc-btn-row{
  display: flex ;
  justify-content: space-between;
  margin:  5% 0;
}
.calc-btn{
  backdrop-filter: blur(5.5px);
  -webkit-backdrop-filter: blur(5.5px);
  background: rgba(255, 255, 255, 0.75);
  border: 1px solid rgba(255, 255, 255, 0.01);
  border-radius: 16px;
  box-shadow: 0 4px 30px rgba(35, 35, 35, 0.1);
  color: black;
  flex-basis: 20%;
  font-family: inherit;
  font-size: 24px;
  height: 65px;
}
.calc-btn:last-child{
  backdrop-filter: blur(5.5px);
  -webkit-backdrop-filter: blur(5.5px);
  background: rgba(255, 255, 255, 0.75);
  border: 1px solid rgba(255, 255, 255, 0.01);
  border-radius: 16px;
  box-shadow: 0 4px 30px rgba(35, 35, 35, 0.1);
  color: black;
  background: orange;
}
.calc-btn:last-child:hover{
  background-color: inherit ;
}
.calc-btn:last-child:active{
  background-color: gray;
}
.double{
  flex-basis: 47%;
}
.tripple{
  flex-basis: 73%;
}
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>


