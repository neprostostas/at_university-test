<template>
    <Header />
    <main class="outer-main">
        <div class="inner-main">
            <slot></slot>
        </div>
    </main>
    <Footer />
</template>

<script>

import { defineComponent } from "vue";
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";

export default defineComponent ({
    name: 'MainLayout',
    components: {
        Footer,
        Header
    },
    setup () {

        return {

        }
    }
});
</script>

<style scoped>

.inner-main {
    padding: 20px 20px 40px;
    max-width: 1200px;
    margin: 0 auto;
}

</style>