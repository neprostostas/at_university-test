<template>

  <div class="info-block">
    <h2>Пройдіть практикум до кінця і на вас чекатимуть 2 подарунки:</h2>
      <div class="columns">
          <div class="column-info">
              <div data-aos="fade-right" data-aos-duration="1000" class="line-block">
                  <img class="cash" src="../assets/cash.svg" alt="cash">
                  <p>+1 потенційний замовник на ваші послуги (прибуток $50−500). Перші гроші і перший досвід із налаштування реклами</p>
              </div>
              <div class="line-block" data-aos="fade-left" data-aos-duration="1000">
                  <img class="gift" src="../assets/gift.svg" alt="gift">
                  <p>Розбір вашого шляху до результатів від куратора (відповіді на питання, розбір реклами, додаткові матеріали та сюрприз)</p>
              </div>
          </div>
          <div class="columns-right">
              <div class="column-info">
                  <img class="stroke-short" src="../assets/stroke-short.svg" alt="stroke-short">
              </div>
              <div class="column-info">
                  <div class="react-block">
                      <img data-aos="zoom-in" data-aos-duration="1000" class="react react-blue" src="../assets/react-blue.svg" alt="react-blue">
                      <img data-aos="zoom-in" data-aos-duration="1200" class="react react-orange" src="../assets/react-orange.svg" alt="react-orange">
                      <img data-aos="zoom-in" data-aos-duration="1400" class="react react-pink" src="../assets/react-pink.svg" alt="react-pink">
                      <img data-aos="zoom-in" data-aos-duration="1600" class="react" src="../assets/react.svg" alt="react">
                      <img data-aos="zoom-in" data-aos-duration="1800" class="react" src="../assets/react.svg" alt="react">
                      <img data-aos="zoom-in" data-aos-duration="2000" class="react" src="../assets/react.svg" alt="react">
                  </div>
                  <p>Зберіть 6 атомів для подарунків</p>
              </div>
          </div>
      </div>
  </div>

</template>

<script>

import { defineComponent } from "vue";

export default defineComponent ({
    name: 'InfoBlock',
    components: {},
    setup () {

        return {

        }
    }
});
</script>

<style scoped>

.info-block h2 {
    text-align: center;
}

.columns {
    display: grid;
    grid-template-columns: minmax(100px, 530px) auto;
    align-items: center;
    gap: 50px;
}

.columns-right {
    display: grid;
    grid-template-columns: 20px auto;
    justify-items: center;
    align-items: center;
    gap: 30px;
}

.info-block {
    padding: 20px 40px;
    max-width: 1160px;
    margin: 0 auto;
    border-radius: 30px;
    background-color: #f5f5f5;
    background-position: center center;
    border-color: transparent;
    border-style: solid;
    box-shadow: 0 40px 16px -30px rgba(0,0,0,0.1);
}

body.dark .info-block {
    background-color: rgba(0, 0, 0, 0.62);;
    color: ;
}

.react-block + p {
    text-align: center;
}

.react-block {
    display: flex;
    flex-wrap: wrap;
    gap: 15px;
}

.react-block img {
    cursor: pointer;
}

.stroke-short {
    height: 150px;
}

.react {
    width: 32px;
}

.gift, .cash {
    width: 38px;
}

.line-block {
    display: grid;
    align-items: center;
    grid-template-columns: auto 1fr;
    gap: 20px;
}

@media (max-width: 775px) {
    .columns {
        grid-template-columns: auto;
        gap: 30px;
    }

    .stroke-short {
        display: none;
    }

    .columns-right {
        gap: 0;
        grid-template-columns: auto;
    }
}

</style>