<template>
    <div class="repo">
        <img :src="getImage" alt="image">
        <h3>{{ title }}</h3>
        <p>{{ description }}</p>
        <a :href="htmlUrl" target="_blank" class="repo-link">View Repository</a>
    </div>
</template>

<script>
export default {
    props: {
        title: String,
        htmlUrl: String,
        id: Number,
        description: String
    },
    computed: {
        getImage() {
            try {
                return new URL(`../assets/imgs/${this.title}.png`, import.meta.url);
            } catch {
                return new URL(`../assets/imgs/default.png`, import.meta.url);
            }

        }
    }
}
</script>

<style scoped>
.repo {
    border: 1px solid #ccc;
    padding: 1rem;
    border-radius: 8px;
    text-align: center;
    transition: transform 0.3s;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    font-family: 'Lato', sans-serif;
}

.repo:hover {
    transform: scale(1.05);
}

.repo-image{
    width: 100%;
    height: auto;
    border-radius: 8px;
    margin-bottom: 1rem;
}

.repo-link{
    text-decoration: none;
    color: purple;
    font-weight: bold;
}

div {
    text-align: center;
    margin: 1rem;
    gap: 1rem;
}

img {
    max-width:200px;
    height: auto;
}
</style>