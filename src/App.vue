<script setup>
import {ref, watchEffect} from "vue"

const darkTheme = ref(false)
const timer = ref(new Date().toLocaleTimeString())

watchEffect(() => {
    setInterval(() => {
        timer.value = new Date().toLocaleTimeString()
    }, 1000)
})

const handleTheme = () => {
    darkTheme.value = !darkTheme.value;
    document.documentElement.style.setProperty('--main-bg-color', darkTheme.value ? "rgba(8, 11, 19, 0.964)" :"rgb(230, 230, 230)")
    document.getElementById("timertext").style.setProperty('--main-text', darkTheme.value ? "rgb(255, 255, 255)" : "rgb(0, 0, 0)")
    document.getElementById("boxbtn").style.setProperty('margin-top', "-200px")
    setTimeout(() => {
        document.getElementById("boxbtn").style.setProperty('margin-top', "0px")
    }, 400)
    setTimeout(() => {
        document.getElementById("boxbtn").style.setProperty('--btn-theme-icon', darkTheme.value ? "url(https://img.icons8.com/office/80/null/bright-moon.png)" : "url(https://img.icons8.com/office/80/null/summer.png)")
    }, 600)
}
</script>

<template>
    <div type="button" @click=handleTheme id="boxbtn"></div>
    <div id="boxtimer">
        <h1 id="timertext">{{timer}}</h1>
    </div>
</template>

<style>
    html {
        --main-bg-color: rgb(230, 230, 230);
        --main-text: rgb(0, 0, 0);
        --btn-theme-icon: url("https://img.icons8.com/office/80/null/summer.png");
        background-color: var(--main-bg-color);
        transition: background-color 1s;
    }

    #app {
        background-color: var(--main-bg-color);
        transition: background-color 1s;
        margin: 10px 0 0 0;
    }

    #boxbtn {
        height: 50px !important;
        width: 50px !important;
        display: grid;
        border-radius: 100%;
        place-items: center;
        margin: 0 0 50px 10px;
        padding: 0 0 0 0;
        content: var(--btn-theme-icon) !important;
        transition: height 0.7s, width 0.7s, opacity 1.5s, margin-top 1s;
        opacity: 0.6;
    }

    #boxbtn:hover {
        height: 55px !important;
        width: 55px !important;
        transition: height 0.7s, width 0.7s, opacity 1.5s, margin-top 1s;
        opacity: 1;
    }

    #boxbtn:active {
        transition:  margin-top 1s;
    }

    #btnthm {
        background-color: var(--btn-theme-color);
        color: var(--main-bg-color);
        height: 150px !important;
        width: 150px !important;
        border-radius: 20%;
    }

    #boxtimer {
        padding: 150px 0 0 0;
        text-align: center;
    }

    #timertext {
        transition: color 1s;
        color: var(--main-text) !important;
    }
    
</style>