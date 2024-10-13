<script setup>
import WelcomeItem from './WelcomeItem.vue'
</script>

<template>
  <div class="welcome">
    <h1>Welcome to My Portfolio!</h1>
    <p>I'm a recent graduate of a full stack bootcamp passionate about working with awesome people to create meaningful
      solutions for others.</p>


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

      Check out my projects in the Portfolio section
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
</style>
