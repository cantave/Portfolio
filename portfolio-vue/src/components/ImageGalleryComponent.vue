<template>
    <div class="slideshow-container">
        <div class="slideshow">
            <transition name="fade">
                <img :key="currentImage" :src="currentImage" alt="Film Photo">
            </transition>
        </div>
        <div class="controls">
            <button @click="prevImage">❮</button>
            <button @click="nextImage">❯</button>
        </div>
    </div>


</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const imageNames = ['1.jpg', '1B.jpg', '1C.jpg', '1D.jpg', '1F.jpg', '2.jpg', '2A.jpg', '2B.jpg',
    '2C.jpg', '2D.jpg', '2E.jpg', '2F.jpg', '3.jpg', '3A.jpg', '3B.jpg', '3C.jpg', '3D.jpg', '3E.jpg',
    '4.jpg', '4A.jpg', '4D.jpg', '5.jpg', '5A.jpg', '5B.jpg', '6.jpg', '7B.jpg', '7A.jpg',
    '8.jpg', '9.jpg', '10.jpg', '10A.jpg', '10B.jpg', '12A.jpg', '12B.jpg', '12C.jpg', '15.jpg', '15A.jpg', '15B.jpg',
    '16A.jpg', '16.jpg', '16A.jpg', '17.jpg', '17A.jpg', '19A.jpg', '20.jpg', '20A.jpg',
    '21A.jpg', '21.jpg', '21B.jpg', '22.jpg', '22A.jpg', '23.jpg', '23A.jpg',
    '24.jpg',
];

const filmPhotos = imageNames.map(name => new URL(`../assets/photos/film/film_travels/${name}`, import.meta.url).href);

const currentIndex = ref(0);
const currentImage = ref(filmPhotos[currentIndex.value]);

const preloadImages = (images) => {
    images.forEach((src) => {
        const img = new Image();
        img.src = src;
    });
};

const nextImage = () => {
    currentIndex.value = (currentIndex.value + 1) % filmPhotos.length;
    currentImage.value = filmPhotos[currentIndex.value];
};

const prevImage = () => {
    currentIndex.value = (currentIndex.value - 1 + filmPhotos.length) % filmPhotos.length;
    currentImage.value = filmPhotos[currentIndex.value];
}

let interval;

const shuffleArray = (array) => {
    for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
    }
};

onMounted(() => {
    shuffleArray(filmPhotos);
    preloadImages(filmPhotos);
    currentImage.value = filmPhotos[currentImage.value];
    interval = setInterval(nextImage, 5000);
});

onUnmounted(() => {
    clearInterval(interval);
})
</script>

<style scoped>
.slideshow-container {
    position: relative;
    max-width: 600px;
    margin: auto;

}

.slideshow {
    max-height: 400px;
    overflow: hidden;
    position: relative;
}

.slideshow img {
    width: 100%;
    height: auto;
    max-height: 400px;
    object-fit: contain;
    border-radius: 8px;
    top: 0;
    left: 0;
    transition: opacity 0.5s ease;

}

.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.5s ease;
}

.fade-enter,
.fade-leave-to {
    opacity: 0;
}

.controls {
    display: flex;
    justify-content: space-between;
    margin-top: 10px;
}

.controls button {
    background-color: rgba(255, 255, 255, 0.8);
    border: none;
    cursor: pointer;
    padding: 10px;
    border-radius: 4px;
    margin: 0 5px;
}

.controls button:hover {
    background-color: rgba(255, 255, 255, 1);
}

.photo-gallery {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
}

.photo-gallery img {
    max-width: 100%;
    height: auto;
    border-radius: 8px;
}
</style>