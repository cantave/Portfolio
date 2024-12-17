<template>
  <div class="music-player">
    <audio ref="audioPlayer" :src="currentTrack" controls @ended="nextTrack"></audio>
  </div>
  <div class="track-info">
    <h3>{{ currentTrackTitle }}</h3>
    <h3>{{ currentArtist }}</h3>

  </div>
  <div class="controls">
    <button @click="prevTrack" :disabled="currentIndex === 0">❮</button>
    <button @click="nextTrack" :disabled="currentIndex === tracks.length - 1">❯</button>
  </div>
</template>

<script setup>
import { onMounted, ref, watch } from 'vue';
import FeelGoodInc from '@/assets/music/Feel Good Inc..mp3';
import Affirmations from '@/assets/music/Affirmations.mp3';
import ComeLiveWithMeAngel from '@/assets/music/Come Live With Me Angel.mp3';
import Thunda from '@/assets/music/Thunda HNNY Remix.mp3';
import CantStop from '@/assets/music/Cant Stop.mp3';
import SuperBoy from '@/assets/music/SUPERBOY.mp3';
import NoseOnTheGrindstone from '@/assets/music/Nose On The Grindstone.mp3';
import Cloudy from '@/assets/music/Cloudy.mp3';

const tracks = [
  {
    title: "Feel Good Inc.",
    artist: "Gorillaz",
    src: FeelGoodInc,

  },
  {
    title: "Affirmations",
    artist: "Girls Of The Internet feat Anelisa Lamola",
    src: Affirmations,
  },
  {
    title: "Come Live With Me Angel",
    artist: "Marvin Gaye",
    src: ComeLiveWithMeAngel,
  },
  {
    title: "Thunda HNNY Remix",
    artist: "Honey Dijon, Tim K feat John Mendelsohn",
    src: Thunda,
  },
  {
    title: "Can't Stop",
    artist: "Red Hot Chili Peppers",
    src: CantStop,
  },
  {
    title: "SUPERBOY",
    artist: "Kid Cudi",
    src: SuperBoy,
  },
  {
    title: "Nose On The Grindstone",
    artist: "Tyler Childers",
    src: NoseOnTheGrindstone,
  },
  {
    title: "Cloudy",
    artist: "DAPHNI",
    src: Cloudy,
  }
];

const currentIndex = ref(0);
const currentTrack = ref(tracks[currentIndex.value].src);
const currentTrackTitle = ref(tracks[currentIndex.value].title);
const currentArtist = ref(tracks[currentIndex.value].artist);
const audioPlayer = ref(null);

function selectRandomTrack() {
  currentIndex.value = Math.floor(Math.random() * tracks.length);
  currentTrack.value = tracks[currentIndex.value].src;
  currentTrackTitle.value = tracks[currentIndex.value].title;
  currentArtist.value = tracks[currentIndex.value].artist;
}

watch(currentIndex, (newIndex) => {
  currentTrack.value = tracks[newIndex].src;
  currentTrackTitle.value = tracks[newIndex].title;
  currentArtist.value = tracks[newIndex].artist;
  audioPlayer.value.load();
});

onMounted(() => {
  selectRandomTrack();
}); 

function nextTrack() {
  if (currentIndex.value < tracks.length - 1) {
    currentIndex.value++;
  }
}

function prevTrack() {
  if (currentIndex.value > 0) {
    currentIndex.value--;
  }
}

</script>

<style scoped>
.music-player {
  margin-top: 2rem;
  display: flex;
  justify-content: center;
}

.track-info {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  margin-top: 1rem;
  font-family: 'Oswald', sans-serif;
}

.controls {
  display: flex;
  justify-content: center;
}

.controls button {
  background-color: rgba(255, 255, 255, 255);
  border: none;
  cursor: pointer;
  padding: 10px;
  border-radius: 4px;
  margin: 0 5px;
}

.controls button:hover {
  background-color: rgba(255, 255, 255, 1);
}
</style>