<template>
<div class="theme-switcher">
    <div class="theme-container">
        <button @click.prevent="changeTheme" class="theme" v-for="(theme,index) in themes" :key="theme.id" :data-index="index" :style="{backgroundColor: theme.colors.background}">
            <span class="theme-name" :style="{color: theme.colors.headline}">{{theme.name}}</span>
            <div class="theme-color-container">
                <div class="theme-colors" :style="{backgroundColor: theme.colors.primary}"></div>
                <div class="theme-colors" :style="{backgroundColor: theme.colors.secondary}"></div>
                <div class="theme-colors" :style="{backgroundColor: theme.colors.tertiary}"></div>
                <div class="theme-colors" :style="{backgroundColor: theme.colors.headline}"></div>
            </div>  
        </button>
    </div>

    <h1>{{title}}</h1>
    <button>Click me</button>
</div>
    
</template>

<style scoped>
    *{
        margin:0;
        padding:0;
        box-sizing: border-box;
    }
    .theme-container{
        display: flex;
        justify-content: space-around;
        align-items: center;
        overflow-x: auto;
    }
    .theme-name{
        flex-basis: 100%;
        padding: 0.2rem 0;
    }
    .theme{
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 0.5rem 0rem 0.75rem 0rem;
        margin: 0 1rem 0 0;
        border-radius: 0.5rem;
        flex-wrap: wrap;
    }
    .theme-color-container{
        display: flex;
    }
    .theme-colors{
        width: 1.25rem;
        height: 1.25rem;
        border-radius: 50%;
        border: 0.15rem solid #fff;
        margin: 0 0 0 -0.2rem;
    }
</style>

<script>
export default {
    name: 'ThemeSwitcher',
    data(){
        return{
            title: 'Colour theme switcher',
        }
    },
    props: {
        themes: Array
    },
    methods:{
        changeTheme: async function(e){
            // Getting the colors of the theme from the props according to the theme button clicked
           const newTheme = this.themes[parseInt(e.target.closest('button').getAttribute("data-index"))].colors
            // Defining the root of the document for cleaner code
           let root = document.documentElement

            // Looping through the colors object and setting the styles in the root
           const entries = Object.entries(newTheme)
           for(let i = 0; i < entries.length; i++){
               for(let j = 1; j < entries[i].length; j++){
            
                   root.style.setProperty(`--${entries[i][0]}`, `${entries[i][1]}`)
                   
               }
           }
           
        }
    }
}
</script>