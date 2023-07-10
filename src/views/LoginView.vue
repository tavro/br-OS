<template>
    <div class="wrapper">
        <div class="login">
            <div class="meta">
                <span>background from</span>
                <span id="url">source.unsplash.com</span>
            </div>
            <div class="content">
                <h1 class="content-header">br/OS</h1>
                <p class="content-text">the browser operating system</p>
                <p class="content-text">your computer on the run</p>
            </div>
            <div class="button-wrapper">
                <RouterLink to="/signup">sign up/log in with email</RouterLink>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { RouterLink } from 'vue-router'

export default {
    name: 'LoginView',
    mounted() {
        document.body.style.backgroundImage = `url(${this.background})`;
    },
    computed: {
        background(): string {
            return "https://source.unsplash.com/random/1920x1080";
        }
    },
}
</script>

<style>
.wrapper {
    height: 100%;
    background-color: rgba(0,0,0,0.5);
    padding: 2rem;
}

.login {
    height: calc(100vh - 4rem);
    display: flex;
    flex-direction: column;
    color: white;
    justify-content: space-between;
}

.meta {
    display: flex;
    flex-direction: column;
}

.content {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.content-text {
    padding: 0px;
    margin: 4px;
    font-size: 20px;
    text-align: center;
}

.button-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: white;
    color: black;
    padding: 8px;
    border-radius: 32px;
    height: 32px;
}

#url {
    font-weight: bold;
}
</style>  

