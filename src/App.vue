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
}
h1{
  color: var(--headline);
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
  border: 0.15rem solid var(--primary);
}

.active{
  border: 0.15rem solid var(--primary);
}
</style>
