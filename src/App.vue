<template>
    <MainLayout>
        <Episode />
        <InfoBlock />
    </MainLayout>
</template>

<script>

import {defineComponent, onMounted} from "vue";
import { createToast } from 'mosha-vue-toastify';
import 'mosha-vue-toastify/dist/style.css'
import MainLayout from "@/components/MainLayout.vue";
import InfoBlock from "@/components/InfoBlock.vue";
import Episode from "@/components/Episode.vue";

export default defineComponent ({
  name: 'App',
  components: {
      Episode,
      InfoBlock,
      MainLayout
  },
  setup () {

    const toast = () => {
        createToast('🌙 Look at NEW night mode! 🌙')
    }

    onMounted(() => {
        toast()
    })

    return {
        toast
    }
  }
});
</script>

<style>

body {
    margin: 0;
    font-family: 'Gilroy', sans-serif;
}

body.dark {
    background: rgba(0, 0, 0, 0.62);
}

body.dark :is(p, h1, h2, h3, a) {
    color: rgba(247, 247, 247, 0.75);
    opacity: 0.7;
}

li {
    list-style: none;
}

@font-face {
    font-family: 'Gilroy';
    src: url('assets/fonts/gilroy/Gilroy-Regular.ttf') format('truetype');
    font-weight: normal;
    font-style: normal;
}


@font-face {
    font-family: 'Gilroy';
    src: url('assets/fonts/gilroy/Gilroy-Bold.ttf') format('truetype');
    font-weight: 700;
    font-style: normal;
}

</style>