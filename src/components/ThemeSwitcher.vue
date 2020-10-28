<template>
<article class="theme-switcher">
    <transition name="fade">
        <section v-show="showThemeSwitcher" class="theme-container">
            <button @click.prevent="changeTheme" class="theme" v-for="(theme,index) in themes" :key="theme.id" :data-index="index" :style="{backgroundColor: theme.colors.background}">
                <span class="theme-name" :style="{color: theme.colors.headline}">{{theme.name}}</span>
                <div class="theme-color-container">
                    <div class="theme-colors" :style="{backgroundColor: theme.colors.primary}"></div>
                    <div class="theme-colors" :style="{backgroundColor: theme.colors.secondary}"></div>
                    <div class="theme-colors" :style="{backgroundColor: theme.colors.tertiary}"></div>
                    <div class="theme-colors" :style="{backgroundColor: theme.colors.headline}"></div>
                </div>  
            </button>
        </section>
    </transition>
    <section class="container">
        <header>
            <h1>{{title}}</h1>
            <button class="icon-button" @click.prevent="showThemeSelector">
                <svg 
                    id="Capa_1" enable-background="new 0 0 512.012 512.012" height="512" viewBox="0 0 512.012 512.012" width="512" xmlns="http://www.w3.org/2000/svg"
                >
                    <g>
                        <path d="m480.006 73h-49v-58c0-8.284-6.716-15-15-15h-320c-8.284 0-15 6.716-15 15v58h-34v-17c0-8.284-6.716-15-15-15s-15 6.716-15 15v72c0 8.284 6.716 15 15 15s15-6.716 15-15v-25h34v57c0 8.284 6.716 15 15 15h320c8.284 0 15-6.716 15-15v-57h34v93.288l-212.638 53.16c-6.678 1.669-11.362 7.669-11.362 14.552v49h-17c-7.921 0-14.477 6.159-14.971 14.064-8.584 137.35-8.029 128.21-8.029 128.936 0 14.657 5.657 28.582 15.931 39.209 21.651 22.4 56.481 22.407 78.139 0 10.273-10.627 15.931-24.552 15.931-39.209 0-.725.554 8.401-8.029-128.936-.494-7.905-7.05-14.064-14.971-14.064h-17v-37.288l212.638-53.16c6.678-1.669 11.362-7.669 11.362-14.552v-120c-.001-8.284-6.717-15-15.001-15z"/>
                    </g>
                </svg>
            </button>
        </header>
        
        <button>I am a button :)</button>

        <p>
            Color theme switcher is a theme switcher built in Vue to add spice to the inherent dark and light modes in the internet with a mix of new palettes from HappyHues.
        </p>

        <p>
            The color theme swithcer is inpired the dark and light trend. I just wanted to add a personal touch to the trend to have the visitors more options than dark and light mode.
        </p>

        <p>
            Prow scuttle parrel provost Sail ho shrouds spirits boom mizzenmast yardarm. Pinnace holystone mizzenmast quarter crow's nest nipperkin grog yardarm hempen halter furl. Swab barque interloper chantey doubloon starboard grog black jack gangway rutters.
            Deadlights jack lad schooner scallywag dance the hempen jig carouser broadside cable strike colors. Bring a spring upon her cable holystone blow the man down spanker Shiver me timbers to go on account lookout wherry doubloon chase. Belay yo-ho-ho keelhaul squiffy black spot yardarm spyglass sheet transom heave to.
        </p>
    </section>
</article>
    
</template>

<script>
export default {
    name: 'ThemeSwitcher',
    data(){
        return{
            title: 'Color theme switcher',
            showThemeSwitcher: false,
        }
    },
    props: {
        themes: Array
    },
    mounted() {
        document.querySelector('.theme').classList.add('active');
    },
    methods:{
        changeTheme: async function(e){
            
           const selectedTheme = e.target.closest('button')

           const newTheme = this.themes[parseInt(selectedTheme.getAttribute("data-index"))].colors

           document.querySelectorAll('.active').forEach(themeSelector => themeSelector.classList.remove('active'))

           selectedTheme.classList.add('active')

           let root = document.documentElement

            // Looping through the colors object and setting the styles in the root
           const entries = Object.entries(newTheme)
           for(let i = 0; i < entries.length; i++){
               for(let j = 1; j < entries[i].length; j++){
                   root.style.setProperty(`--${entries[i][0]}`, `${entries[i][1]}`)   
               }
           }
           
        },
        showThemeSelector(){
            this.showThemeSwitcher = !this.showThemeSwitcher
        }
    }
}
</script>

<style scoped>
    .fade-enter-active, .fade-leave-active {
        transition: opacity .3s;
    }
    .fade-enter, .fade-leave-to{
        opacity: 0;
    }
    .theme-container{
        display: flex;
        justify-content: space-around;
        align-items: center;
        padding: 2rem;
        flex-wrap: wrap;
    }
    .theme-name{
        flex-basis: 100%;
        padding: 0.2rem 0;
    }
    .theme{
        cursor: pointer;
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 0.5rem 0rem 0.75rem 0rem;
        margin: 0.5rem;
        border-radius: 0.75rem;
        flex-wrap: wrap;
        width: 8rem;
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
    .container{
        padding: 4rem 16rem;
        margin: 0 auto;
    }
    h1{
        margin: 1rem 0;
    }
    button{
        margin: 1rem 0;
        padding: 1.25rem 2.5rem;
        border-radius: 0.5rem;
    }
    p{
        margin: 1rem 0;
        text-align: justify;
    }
    .container header{
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    .icon-button{
        margin: 0;
        border-radius: 50%;
        padding: 1rem;
        display: flex;
        place-items: center;
    }
    .icon-button svg{
        width: 1.25rem;
        height: 1.25rem;
    }
</style>