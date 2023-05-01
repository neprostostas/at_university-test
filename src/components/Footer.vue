<template>

    <footer class="outer-footer">
        <div class="inner-footer">

            <div class="column-footer">
                <img class="logo-footer" src="../assets/logo-footer.png" alt="logo-footer">
                <a href="#">Політика конфіденційності</a>
                <p>© {{new Date().getFullYear()}} Atom. Усі права захищені</p>
            </div>
            <div class="column-footer">
                <h3>Наша місія</h3>
                <p>Створити доступне з будь-якої точки світу висококласне, трансформаційне навчання із засвоєння digital-професій та заробітку на них</p>
            </div>
            <div class="column-footer">
                <h3>Контакти</h3>
                <a href="tel:0800334125">0 800 33 41 25</a>
                <a href="mailto:info@at.university">info@at.university</a>
                <p class="address-text">м. Київ, вул. Князів Острозьких, 2</p>
            </div>

        </div>
    </footer>

</template>

<script>

import { defineComponent } from "vue";

export default defineComponent ({
    name: 'Footer',
    components: {},
    setup () {

        return {

        }
    }
});
</script>

<style scoped>

a, p {
    color: #ffffff;
    font-size: 12px;
    line-height: 1.55;
    font-weight: 400;
    letter-spacing: 0.5px;
    opacity: 0.3;
}

h3 {
    color: #ffffff;
    font-weight: 400;
    opacity: 0.3;
    font-size: 16px;
}

.outer-footer {
    background: #050505;
}

.inner-footer {
    background: #050505;
    padding: 50px 20px 40px;
    max-width: 1200px;
    margin: 0 auto;

    display: grid;
    grid-template-columns: repeat(3, 33.333%);
    align-items: center;
    justify-items: center;
    justify-content: space-between;
    gap: 10px;
}

.column-footer:nth-child(1) {
    display: grid;
    justify-items: start;
}

.column-footer:nth-child(2) {
    display: grid;
    justify-items: center;
    text-align: center;
}

.column-footer:nth-child(3) {
    display: grid;
    justify-items: end;
}

.logo-footer {
    padding-bottom: 20px;
    position: relative;
    left: -7px;
    width: 120px;
}

@media (max-width: 700px) {

    .inner-footer {
        grid-template-columns: repeat(2, auto);
        align-items: center;
        justify-items: center;
        justify-content: center;
        gap: 50px;
    }

    .column-footer:nth-child(2) {
        display: none;
    }

}

@media (max-width: 530px) {

    .inner-footer {
        grid-template-columns: repeat(2, auto);
        gap: 10px;
    }

    .address-text {
        text-align: right;
    }

}

</style>