<template>
    <div class="wrapper">
        <div class="signup">
            <div class="input-wrapper">
                <h1>enter email to sign up/log in</h1>
                <input id="email" type="text" placeholder="email" />
            </div>
            <div class="button-wrapper">
                <RouterLink to="/home">sign up/log in</RouterLink>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { RouterLink } from 'vue-router'
export default {
    name: 'SignupView',
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

.signup {
    height: calc(100vh - 4rem);
    display: flex;
    flex-direction: column;
    color: white;
    justify-content: space-between;
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

#email {
    padding: 8px;
    border-radius: 16px;
    height: 16px;
    border: 0;
    background-color: rgba(255,255,255,0.8);
    color: white;
    text-align: left;
}
</style>  

