<template>
    <nav class="navbar">
        <ul>
            <li>
                <RouterLink to="/" :class="{ active: isActive('/')}">Home</RouterLink>
            </li>
            <li>
                <RouterLink to="/about" :class="{ active: isActive('/about')}">About</RouterLink>
            </li>
            <li>
                <RouterLink v-bind:to="{ name: 'portfolio' }" :class="{ active: isActive('/portfolio')}">Portfolio</RouterLink>
            </li>
            <li>
                <RouterLink :to="{ name: 'resume' }" :class="{ active: isActive('/resume')}">Resume</RouterLink>
            </li>
        </ul>
    </nav>
</template>

<script>
import { RouterLink, useRoute } from 'vue-router';
export default {
    components: {
        RouterLink,
    },
    setup() {
        const route = useRoute();

        const isActive = (path) => {
            return route.path === path;
        };

        return {isActive};
    }
}
</script>

<style scoped>
.navbar {
    background-color: white;
    padding: 1rem;
}

.navbar ul {
    list-style-type: none;
    display: flex;
    gap: 1rem;
}

.navbar a {
    color: black;
    text-decoration: none;
}

.navbar a:hover {
    text-decoration: underline;
}

.navbar a.active {
    color: purple;
    font-weight: bold;
}
</style>