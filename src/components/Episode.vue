<template>
    <div class="tab-content" v-for="(lesson, index) in lessonsData" :key="index" :class="{ active: index === currentTab }">
        <div class="text-center">
            <h1><span class="orange">Episode {{index+1}}.</span> {{lesson?.subtitle}}</h1>
        </div>
    </div>

    <div class="videos-content">
        <div data-aos="fade-right" data-aos-duration="1000" class="tab-content content" v-for="(lesson, index) in lessonsData" :key="index" :class="{ active: index === currentTab }">
            <div>
                <ul>
                    <li>
                        <h2>{{ lesson?.title }}</h2>
                        <h3>{{ lesson?.subtitle }}</h3>
                        <p class="text-description">{{ lesson?.description }}</p>
                        <iframe width="560" height="315" :src="`https://www.youtube.com/embed/${lesson?.video_url}`" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen @play="playVideo()" @pause="pauseVideo()"></iframe>
                    </li>
                </ul>
            </div>
        </div>

        <div data-aos="fade-left" data-aos-duration="1000" class="tabs">
            <button class="tab" v-for="(lesson, index) in lessonsData" :key="index" :class="{ active: index === currentTab }" @click="currentTab = index">{{index+1}}. {{lesson.title}}</button>
        </div>
    </div>

    <div class="next-container">
        <div class="tab-content content" v-for="(lesson, index) in lessonsData" :key="index" :class="{ active: index === currentTab }">
            <div class="known-block">
                <div data-aos="fade-up-right" data-aos-duration="1000" class="column-info">
                    <img class="img-text1" src="../assets/text1.svg" alt="text1">
                    <img class="img-text2" src="../assets/text2.svg" alt="text2">

                    <ul v-for="(item, ind) in lesson.info" :key="ind">
                        <li>{{ind+1}}. {{ item }}</li>
                    </ul>
                </div>

                <div data-aos="fade-up-left" data-aos-duration="1000" class="columns-right">
                    <img class="stroke-long" src="../assets/stroke-long.svg" alt="stroke-long">
                    <div class="column-info">
                        <p class="ready-text">Вже переглянули? Отримайте доступ до наступного:</p>
                        <button class="nextVideo-btn" :disabled="!isNextLessonAvailable" @click="openNextLesson()">Наступний епізод</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

import { defineComponent, ref } from "vue";
import lessonsData from '../data/info.json'

export default defineComponent ({
    name: 'Episode',
    components: {},
    setup () {

        const currentTab = ref(0);

        const videoTimer = ref(0);
        const isVideoPlaying = ref(false);
        const isNextLessonAvailable = ref(false);

        const startTimer = () => {
            videoTimer.value = setInterval(() => {
                if (isVideoPlaying.value) {
                    const remainingTime = lessonsData[currentTab.value]?.video_time - videoTimer.value;
                    console.log(`${videoTimer.value}/${lessonsData[currentTab.value]?.video_time} (${remainingTime} seconds left)`);
                    if (videoTimer.value >= lessonsData[currentTab.value]?.video_time) {
                        isNextLessonAvailable.value = true;
                        clearInterval(videoTimer.value);
                    } else {
                        videoTimer.value += 1;
                    }
                }
            }, 1000);
        };

        const playVideo = () => {
            isVideoPlaying.value = true;
            startTimer();
        };

        const pauseVideo = () => {
            isVideoPlaying.value = false;
            clearInterval(videoTimer.value);
        };

        const openNextLesson = () => {
            if (isNextLessonAvailable.value) {
                currentTab.value += 1;
                isNextLessonAvailable.value = false;
            }
        };

        return {
            lessonsData,
            currentTab,

            videoTimer,
            isVideoPlaying,
            isNextLessonAvailable,
            startTimer,
            playVideo,
            pauseVideo,
            openNextLesson,
        }
    }
});
</script>

<style scoped>

ul {
    padding: 0;
}

.columns-right {
    display: grid;
    grid-template-columns: 20px auto;
    justify-items: center;
    align-items: center;
    gap: 30px;
}

.ready-text {
    text-align: center;
}

.text-description {
    max-width: 560px;
}

.nextVideo-btn {
    cursor: pointer;
    width: -webkit-fill-available;
    padding: 10px 20px;
    color: #ffffff;
    font-size: 16px;
    line-height: 1.55;
    font-weight: 500;
    border-width: 2px;
    background-color: #f8871f;
    border-color: transparent;
    border-style: solid;
    transition: background-color 0.2s ease-in-out, color 0.2s ease-in-out, border-color 0.2s ease-in-out;
}

.nextVideo-btn:disabled {
    background: #bababa;
    cursor: auto;
}

.stroke-long {
    height: 280px;
}

.known-block {
    margin: 20px 0 40px;
    display: grid;
    grid-template-columns: minmax(100px, 570px) auto;
    align-items: center;
    gap: 50px;
}

.videos-content {
    display: grid;
    grid-template-columns: repeat(2, auto);
    align-items: start;
    gap: 60px;
}

.text-center {
    text-align: center;
}

.text-center > h1 {
    padding-bottom: 30px;
    font-size: 24px;
    font-weight: 400;
}

.orange {
    color: rgb(248, 135, 31);
}

.tabs {
    display: grid;
    gap: 20px;
}

.tab {
    cursor: pointer;
    padding: 20px;
    color: #f8871f;
    font-size: 18px;
    line-height: 1.15;
    font-weight: 500;
    border-width: 2px;
    background-color: #ffffff;
    border-color: #f8871f;
    border-style: solid;
    transition: background-color 0.2s ease-in-out, color 0.2s ease-in-out, border-color 0.2s ease-in-out;
}

.tab.active {
    cursor: auto;
    background-color: #f8871f;
    color: #ffffff;
}

body.dark .tab {
    background-color: #413c3c;
}

body.dark .tab.active {
    background-color: #f8871f;
    color: rgba(247, 247, 247, 0.75);
}

.tab-content {
    display: none;
}

.tab-content.active {
    display: block;
}

.img-text1 {
    width: 230px;
    padding-right: 20px;
}

.img-text2 {
    width: 210px;
}

@media (max-width: 930px) {

    iframe {
        margin-top: 30px;
        width: calc(100% - 80px);
    }

    .videos-content {
        grid-template-columns: auto;
        gap: 20px;
    }

    .tab-content.content {
        text-align: center;
    }

    .text-description {
        margin: 0 auto;
        text-align: center;
    }

    .text-center > h1 {
        padding-bottom: 10px;
    }

    .known-block {
        margin: 40px 0;
    }
}

@media (max-width: 700px) {

    .stroke-long {
        display: none;
    }

    .known-block {
        grid-template-columns: auto;
        gap: 0;
    }

    .ready-text {
        font-weight: 700;
    }

    .columns-right {
        grid-template-columns: auto;
        gap: 30px;
    }

    .tab {
        padding: 15px 10px;
    }

}

@media (max-width: 685px) {

    iframe {
        margin-top: 30px;
        width: calc(100% - 40px);
    }

}

@media (max-width: 620px) {

    iframe {
        margin-top: 30px;
        width: calc(100% - 5px);
    }

}

</style>