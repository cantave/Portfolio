<template>
    <div class="resume">
        <iframe src="/resume.pdf" title="Resume PDF" style="width: 100%; height: 500px; border: none;"> </iframe>
        <p v-if="!resume"> Resume not found. Please check the path.</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            resume: '/resume.pdf'
        }
    },
    mounted() {
        console.log(this.resume)
    }
}

</script>

<style scoped>
.resume {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    max-height: 75vh;
    overflow: hidden;
    padding-top: 20px;
}

iframe {
    display: block;
    width: 100%;
    height: 400px;
    border: none;
    overflow-y: auto;

}


@media (max-width: 500px) {
    iframe {
        height: 300px;
        width: 100%;
    }
}
</style>