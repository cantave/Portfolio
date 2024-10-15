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
            <li>
                <RouterLink :to="{ name: 'contact' }" :class="{ active: isActive('/contact')}">Contact</RouterLink>
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
    flex-wrap: wrap;
    gap: 1rem;
    padding: 0;
    margin: 0%;
}

.navbar a {
    color: black;
    text-decoration: none;
    transition: transform 0.2s ease, text-decoration 0.2s ease;
}

.navbar a:hover {
    text-decoration: underline;
    transform: scale(1.1);
}

.navbar a.active {
    color: purple;
    font-weight: bold;
}

@media (max-width: 500px){
    .navbar ul {
        flex-direction: column;
        align-items: flex-end;
        gap: 0.5rem;
    }

    .navbar {
        padding: 0.5rem;
    }
}
</style>