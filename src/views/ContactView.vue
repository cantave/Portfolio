<template>
    <div class="contact-container">
        <h2> Contact Me</h2>
        <img class="headshot" :src="headshotUrl" alt="Headshot">
        <form action="https://formsubmit.co/ad80873878273ad630f19f7d98a25718" method="POST">
            <div class="form-group">
                <label for="name">Name:</label>
                <input type="text" id="name" name="name" v-model="form.name" required />
            </div>
            <div class="form-group">
                <label for="email">Email:</label>
                <input type="email" id="email" name="email" v-model="form.email" required />
            </div>
            <div class="form-group">
                <label for="message">Message:</label>
                <textarea v-model="form.message" id="message" name="message" required></textarea>
            </div>
            <input type="hidden" name="_next" value="https://marvencantave.netlify.app/">
            <input type="hidden" name="_captcha" value="false">
            <button type="submit">Send Message</button>
        </form>
        <div v-if="successMessage">{{ successMessage }}</div>
        <div v-if="errorMessage" class="error">{{ errorMessage }}</div>
    </div>
</template>

<script>
import Headshot from '@/assets/photos/Headshot.jpeg';

export default {
    data() {
        return {
            form: {
                name: '',
                email: '',
                message: '',
            },
            successMessage: '',
            errorMessage: '',
            headshotUrl: Headshot,
        };
    },
};
</script>

<style scoped>
.contact-container {
    max-width: 600px;
    margin: auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 0 20px;
}

h2 {
    font-size: 2rem;
    font-family: 'Lato', sans-serif;
}

.headshot {
    width: 100px;
    border-radius: 50%;
    margin: 1rem;
}

form {
    display: flex;
    flex-direction: column;
    row-gap: 1rem;
    width: 100%;
}

.form-group {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    width: 100%;
}

label {
    font-family: 'Oswald', sans-serif;
    padding-right: 10px;
    font-weight: bold;
}

input,
textarea,
button {
    background-color: whitesmoke;
    border-radius: 8px;
    width: 100%;
    padding: 0.5rem;
    font-family: 'Oswald', sans-serif;
}

button {
    font-weight: bold;
    border: black;
    text-decoration: black;
}

button:hover {
    cursor: pointer;
}

@media (max-width: 500px) {
    .contact-container {
        padding: 0 15px;
    }
}


</style>