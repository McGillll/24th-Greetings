<template>
    <Head>
        <Title>Video Greeting</Title>
    </Head>
    <div class="min-h-screen bg-gradient-to-br from-pink-200 via-purple-200 to-blue-200 px-4 py-10 flex flex-col items-center">
        <div class="w-full max-w-4xl text-center">
            <h1 class="text-3xl sm:text-4xl md:text-5xl font-bold text-gray-800 mb-8">
                To my BORTDI GURL
            </h1>
            <p class="text-base sm:text-lg md:text-xl text-gray-700 mb-12">
                A little something special for your day 💕
            </p>

            <!-- First Video -->
            <div class="mb-12">
                <h2 class="text-xl sm:text-2xl font-semibold text-gray-800 mb-4">
                    A Song Just for You 🎶
                </h2>
                <div class="flex justify-center">
                    <video
                        src="/videos/Song.mp4"
                        controls
                        class="w-full max-w-md rounded-xl shadow-lg"
                    ></video>
                </div>
            </div>

            <!-- Second Video -->
            <div>
                <h2 class="text-xl sm:text-2xl font-semibold text-gray-800 mb-4">
                    A Short Greetings and Wishes 💌
                </h2>
                <div class="flex justify-center">
                    <video
                        src="/videos/Greetings.mp4"
                        controls
                        class="w-full max-w-md rounded-xl shadow-lg"
                    ></video>
                </div>
            </div>
        </div>
                    <!-- Back Button -->
            <div class="mt-8">
                <button
                    @click="navigateTo('/')"
                    class="px-6 py-3 bg-pink-500 hover:bg-pink-600 text-white rounded-full shadow-lg transition"
                >
                    Back
                </button>
            </div>
    </div>
</template>
