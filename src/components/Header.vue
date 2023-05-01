<template>

    <header class="outer-header">

        <div class="inner-header">
            <div class="top-block">
                <img data-aos="fade-down" data-aos-duration="700" class="logo" src="../assets/logo.svg" alt="logo">
                <div data-aos="zoom-in-down" data-aos-duration="1000" class="theme-switcher" @click="toast">
                    <svg v-if="theme === 'light'" @click="setTheme('dark')" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <circle cx="12" cy="12" r="5"></circle>
                        <line x1="12" y1="1" x2="12" y2="3"></line>
                        <line x1="12" y1="21" x2="12" y2="23"></line>
                        <line x1="4.22" y1="4.22" x2="5.64" y2="5.64"></line>
                        <line x1="18.36" y1="18.36" x2="19.78" y2="19.78"></line>
                        <line x1="1" y1="12" x2="3" y2="12"></line>
                        <line x1="21" y1="12" x2="23" y2="12"></line>
                        <line x1="4.22" y1="19.78" x2="5.64" y2="18.36"></line>
                        <line x1="18.36" y1="5.64" x2="19.78" y2="4.22"></line>
                    </svg>
                    <svg v-else @click="setTheme('light')" class="moon-icon" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"></path>
                    </svg>
                </div>
            </div>
            <h1 data-aos="zoom-in" data-aos-duration="1000">Як заробляти <span class="stroke-container"><img class="stroke" src="../assets/stroke.png" alt="stroke"> від $100</span> на день на налаштуванні рекламних кампаній Facebook+Instagram</h1>
        </div>

    </header>

</template>

<script>

import { defineComponent, onBeforeMount, onMounted, ref } from 'vue'
import {createToast} from "mosha-vue-toastify";

import AOS from 'aos'
import 'aos/dist/aos.css'

export default defineComponent ({
    name: 'Header',
    components: {

    },
    setup () {

        const toast = () => {
            const theme = localStorage.getItem('theme')
            if (theme === 'light') {
                createToast('☀️ You are on day mode! ☀️')
            } else {
                createToast('🌙 You are on night mode! 🌙')
            }
        }

        const theme = ref('light')

        // Save the theme in local storage so that it persists across page refreshes
        function setTheme(t) {
            theme.value = t
            localStorage.setItem('theme', t)
            document.body.className = theme.value
        }

        onBeforeMount(()=>{
            document.body.className = localStorage.getItem('theme')
        })

        onMounted(()=>{

            AOS.init()

            // Check if there is a saved theme in local storage and set it
            const savedTheme = localStorage.getItem('theme')
            if (savedTheme) {
                theme.value = savedTheme
            }
        })

        return {
            theme, setTheme, toast
        }
    }
});
</script>

<style scoped>

.theme-switcher {
    cursor: pointer;
}

.top-block {
    display: grid;
    grid-template-columns: repeat(2, auto);
    align-items: center;
    justify-items: center;
    justify-content: center;
    gap: 30px;
}

.inner-header {
    padding: 50px 20px 20px;
    text-align: center;
    max-width: 1200px;
    margin: 0 auto;
}

.inner-header h1 {
    padding-top: 30px;
    max-width: 1065px;
    display: block;
    margin: 0 auto;
    color: #000000;
    font-size: 36px;
    line-height: 1.25;
    font-weight: 700;
    background-position: center center;
}

.inner-header h1 span {
    color: rgb(248, 135, 31);
}

.logo {
    width: 100px;
}

.stroke-container {
    position: relative;
}

.stroke {
    width: 180px;
    position: absolute;
    top: -20px;
    left: -30px;
    z-index: 1;
    transform: scale(0.9);
}


@media (max-width: 460px) {

    .inner-header h1 {
        font-size: 30px;
    }

    .stroke {
        width: 180px;
        position: absolute;
        top: -20px;
        left: -100px;
    }

}

</style>