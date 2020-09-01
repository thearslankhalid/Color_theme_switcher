<template>
  <div id="app">
    <ThemeSwitcher  :themes = "themes" />
  </div>
</template>

<script>
import json from './assets/theme.json'
import ThemeSwitcher from './components/ThemeSwitcher.vue'

export default {
  name: 'App',
   data(){
    return{
      themes : json
    }
  },
  components: {
    ThemeSwitcher
  } 
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Open+Sans&family=Teko:wght@700&display=swap');
  *{
    margin:0;
    padding:0;
    box-sizing: border-box;
  }
  :root{
    --primary: #ffd803;
    --secondary: #e3f6f5;
    --tertiary: #bae8e8;
    --headline: #272343;
    --buttonText: #272343;
    --paragraphText:#2d334a;
    --background: #fffffe;
  }
  body{
    background-color: var(--background);
    font-family: 'Open Sans', sans-serif;
    line-height: 1.5rem;
    position: relative;
  }
  h1{
    color: var(--headline);
    font-family: 'Teko', sans-serif;
    font-size: 3rem;
    line-height: 3rem;
  }
  p{
    color: var(--paragraphText);
  }
  button{
    color: var(--buttonText);
    background-color: var(--primary); 
    border: none;
  }
  button:focus{
    outline: none;
  }
  .theme-container{
    background-color: var(--primary);
  }
  .theme{
    border: 0.13rem solid transparent;
  }
  .active{
    border-color: var(--headline);
  }
  .icon-button svg{
    fill: var(--buttonText);
  }
</style>
