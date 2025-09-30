<template>
    <div class="min-h-screen flex items-center justify-center bg-gradient-to-br from-pink-200 via-purple-200 to-blue-200 px-4">
        <div class="text-center w-full max-w-md">
            <h1 class="text-4xl sm:text-5xl md:text-5xl font-bold text-gray-800 mb-6 leading-tight">
                Happy Birthday, Cherry Eam 🎉
            </h1>
            <p class="text-base sm:text-lg md:text-xl text-gray-700 mb-8 leading-relaxed">
                Wishing you a day filled with love, laughter, and all the things that make you smile.
            </p>

            <button
                @click="revealSurprise"
                class="w-full sm:w-auto px-6 py-3 bg-pink-500 hover:bg-pink-600 text-white rounded-full shadow-lg transition"
            >
                Tap for a Surprise
            </button>

            <transition name="fade">
                <div
                    v-if="showMessage1"
					@click="navigateTo('/photoSlide')"
                    class="mt-6 sm:mt-8 bg-white hover:bg-pink-300 transition-all shadow-xl rounded-2xl p-4 sm:p-6 text-gray-800"
                >
                    <p class="text-lg sm:text-xl leading-relaxed">
                        You are the best part of my life. I’m grateful for you every day ❤️
                    </p>
					<span class="text-black/20 text-sm">Click Here</span>
                </div>
            </transition>
            <transition name="fade">
                <div
                    v-if="showMessage1"
					@click="navigateTo('/videoGreeting')"
                    class="mt-6 sm:mt-8 bg-white hover:bg-pink-300 transition-all shadow-xl rounded-2xl p-4 sm:p-6 text-gray-800"
                >
                    <p class="text-lg sm:text-xl leading-relaxed">
                        Greetings from the dev!!!
                    </p>
					<span class="text-black/20 text-sm">Click Here</span>
                </div>
            </transition>

            <transition name="fade">
                <div
                    v-if="showMessage2"
					@click="navigateTo('/flowers')"
                    class="mt-4 sm:mt-6 bg-white shadow-xl hover:bg-pink-300 transition-all duration-1000 rounded-2xl p-4 sm:p-6 text-gray-800"
                >
                    <p class="text-lg sm:text-xl leading-relaxed">
                        <span class="font-bold">
							Proverbs 31:10-30
						</span>
                    </p>
                </div>
            </transition>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue'

const showMessage1 = ref(false)
const showMessage2 = ref(false)

const revealSurprise = () => {
    showMessage1.value = true
    setTimeout(() => {
        showMessage2.value = true
    }, 500)
}
</script>

<style>
.fade-enter-active, .fade-leave-active {
    transition: opacity 0.5s;
}
.fade-enter-from, .fade-leave-to {
    opacity: 0;
}
</style>
