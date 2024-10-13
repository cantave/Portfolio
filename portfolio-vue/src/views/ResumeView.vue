<template>
    <div class="resume">
        <embed :src="resume" />
    </div>
</template>

<script>
import pdf from '../assets/resume.pdf'

export default {
    data() {
        return {
            resume: pdf
        }
    }
}

</script>

<style scoped>
embed {
    width: 70vw;
    height: 100vh;
    border: none;

}

.resume {
    display: flex;
    justify-content: center;
    max-height: 75vh;
    overflow-y: auto;
    padding-top: 20px;
}
</style>