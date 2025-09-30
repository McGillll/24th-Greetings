<template>
    <div class="min-h-screen flex items-center justify-center bg-gradient-to-br from-blue-200 via-purple-200 to-pink-200 px-4">
        <div class="w-full max-w-2xl text-center">
            <h1 class="text-3xl sm:text-4xl md:text-5xl font-bold text-gray-800 mb-8">
                Our Memories Together ❤️
            </h1>

            <!-- Slideshow Container -->
            <div class="relative overflow-hidden rounded-2xl shadow-lg">
                <transition name="fade" mode="out-in">
                    <img
                        :key="slides[currentIndex].src"
                        :src="slides[currentIndex].src"
                        alt="slideshow image"
                        class="w-full h-64 sm:h-80 md:h-96 object-contain"
                    />
                </transition>
            </div>

            <!-- Message -->
            <transition name="fade" mode="out-in">
                <p
                    :key="slides[currentIndex].message"
                    class="mt-6 text-lg sm:text-xl text-gray-800 leading-relaxed"
                >
                    {{ slides[currentIndex].message }}
                </p>
            </transition>

            <!-- Indicators -->
            <div class="flex justify-center mt-4 space-x-2">
                <span
                    v-for="(slide, index) in slides"
                    :key="index"
                    @click="goToSlide(index)"
                    class="w-3 h-3 rounded-full cursor-pointer"
                    :class="currentIndex === index ? 'bg-pink-500' : 'bg-gray-400'"
                ></span>
            </div>

            <!-- Back Button -->
            <div class="mt-8">
                <button
                    @click="goBack"
                    class="px-6 py-3 bg-pink-500 hover:bg-pink-600 text-white rounded-full shadow-lg transition"
                >
                    Back
                </button>
            </div>
        </div>

        <!-- Background Audio -->
        <audio ref="bgAudio" src="/audios/yung kai - blue (official music video).mp3" loop></audio>
    </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

const slides = [
    { src: '/images/1.jpg', message: 'Pers detdet' },
    { src: '/images/2.jpg', message: 'Sweet ang ferson dre guys' },
    { src: '/images/3.jpeg', message: 'Second detdet, ulaw pang mga persons' },
    { src: '/images/4.jpeg', message: 'Cutie ang person hehe' },
    { src: '/images/5.jpg', message: 'Third detdet, 30% picnic 70% baktas' },
    { src: '/images/6.jpg', message: 'HAHAHAHA Lupang hinirang' },
    { src: '/images/7.jpg', message: 'Gipang kapoy nami dre guys' },
    { src: '/images/8.jpg', message: 'Devo daw kunuhay nag tabi radiay tu' },
    { src: '/images/9.jpg', message: 'Fourth detdet, nag museum ang mga fersons' },
    { src: '/images/10.jpg', message: 'Gikan ni shag maoy ani dre guys' },
    { src: '/images/11.jpg', message: 'Ganahan sha sakong braso guys' },
    { src: '/images/12.jpeg', message: 'Yiiee Graduation, dako na akong bb' },
    { src: '/images/13.jpeg', message: 'Ulaw, nay nagpapic sako HEHE' },
    { src: '/images/14.jpeg', message: 'Gitudluan ko nilag magic dre sa inasal saon pag unli rice' },
    { src: '/images/15.jpeg', message: 'Nanapuy nagpapic saako guys' },
    { src: '/images/16.jpeg', message: 'Atubang ang lalaki sa pamilya sa babae HUHU ulaw gilibrehan ko' },
    { src: '/images/17.jpeg', message: 'Detdet kauban ang mama sa laki (Way lami dre na samgyup)' },
    { src: '/images/18.jpeg', message: 'HAHAHAHAHAHAHA' },
    { src: '/images/19.jpeg', message: 'Nagsabay2 si Mae Ann ug Glenn HAHAHA' },
    { src: '/images/20.jpg', message: 'Busy grinderist era na sakong bb. Blessings to you po <3' },
    { src: '/images/21.jpeg', message: 'Pinaka daghag toyo na detdet wa ni talab ang pagkaon HAHAHA' },
    { src: '/images/22.jpeg', message: 'Call bisag nay kanya2 gna buhat era' },
    { src: '/images/23.jpg', message: 'Yiiee holding hands daw' },
    { src: '/images/24.jpeg', message: 'Happy Birthday friti little busy short tempered blessed bb <3' }
]

const currentIndex = ref(0)
let intervalId = null

const goToSlide = (index) => {
    currentIndex.value = index
}

const startSlideshow = () => {
    intervalId = setInterval(() => {
        currentIndex.value = (currentIndex.value + 1) % slides.length
    }, 5000) // 5 seconds
}

const stopSlideshow = () => {
    if (intervalId) clearInterval(intervalId)
}

const goBack = () => {
    router.back()
}

// Autoplay audio
const bgAudio = ref(null)
onMounted(() => {
    startSlideshow()

    const playAudio = () => {
        if (bgAudio.value) {
            bgAudio.value.muted = false
            bgAudio.value.play()
        }
        document.removeEventListener('click', playAudio)
    }

    if (bgAudio.value) {
        bgAudio.value.play().catch(() => {
            document.addEventListener('click', playAudio)
        })
    }
})

onBeforeUnmount(() => {
    stopSlideshow()
})
</script>

<style>
.fade-enter-active, .fade-leave-active {
    transition: opacity 1s ease;
}
.fade-enter-from, .fade-leave-to {
    opacity: 0;
}
</style>
