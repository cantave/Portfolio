<script setup>
import PortfolioView from '@/views/PortfolioView.vue';
import WelcomeItem from './WelcomeItem.vue'
import { RouterLink } from 'vue-router';
</script>

<template>
  <div class="welcome">
    <h1>Welcome to My Portfolio!</h1>
    <p>I'm a recent graduate of a full stack bootcamp passionate about working with awesome people to create meaningful
      solutions for others. I am currently looking for a junior dev role so reach out if you have some leads!😁</p>


    <WelcomeItem>

      <template #icon>
        <i class="icon">🛠️</i>
      </template>

      <template #heading>About Me</template>

      I enjoy working with modern web technologies and always strive to learn more.

    </WelcomeItem>

    <WelcomeItem>

      <template #icon>
        <i class="icon">📂</i>
      </template>

      <template #heading>My Projects</template>
      I've mostly been working on some small projects to reinforce what I've learned at the bootcamp,
        but my goal in the next few months is to build a CRUD app.
      Check out my projects in the <RouterLink to="/portfolio">Portfolio</RouterLink> section.

    </WelcomeItem>

    <WelcomeItem>

      <template #icon>
        <i class="icon">📸</i>
      </template>

      <template #heading>Photography</template>

      If you hadn't noticed by now, one of my hobbies is photography (say cheese!). I enjoy it because it give me the
      opportunity to show you the world from my perspective.
    </WelcomeItem>

    <WelcomeItem>

      <template #icon>
        <i class="icon">🎶</i>
      </template>

      <template #heading>Music</template>

      Listening to and playing music are also interests of mine! I enjoy sharing and discovering new sounds/genres - it
      feels like giving my emotions a voice.
      I also play the 🎸 and I'm a decent singer. Know that I'm always down for some karaoke 🎤.
    </WelcomeItem>

  </div>

</template>

<style scoped>
.welcome {
  max-width: 600px;
  text-align: center;
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  color: black;
  font-family: 'Lato', sans-serif;

}

p {
  font-size: 1.2rem;
  margin-bottom: 2rem;
  font-family: 'Lato', sans-serif;
}

.icon {
  font-size: 2rem;
}

a {
  text-decoration: none;
  color: black;
}

a:hover {
  transition: scale(1.05);
  color: purple;
}

.body {
  font-family: 'Source Sans Pro', sans-serif;
}
</style>
