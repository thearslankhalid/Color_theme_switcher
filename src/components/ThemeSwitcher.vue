<template>
<div class="theme-container">
    <h1>This is theme number {{ themes }} </h1>
    <ul >
        <li>Theme div here</li>
    </ul>
</div>
    
</template>

<style scoped>
    h1{
        color: blueviolet;
    }
</style>

<script>

import * as themes from '../assets/theme.json'
export default {
    name: 'ThemeSwitcher',
    props:{
        theme: Number,
        themes: themes
    }
}
</script>