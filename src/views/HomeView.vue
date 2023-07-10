<template>
    <div class="wrapper">
        <div class="home">
            <div>
                <h1>welcome home!</h1>
                <p>choose your machine in the list</p>
            </div>
            <div class="list">
                <h2>your machines</h2>
                <p>you don't have any machines yet, but you can still browse <RouterLink to="/browse" id="local">your local computer</RouterLink></p>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { RouterLink } from 'vue-router'
export default {
    name: 'HomeView',
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

.home {
    height: calc(100vh - 4rem);
    display: flex;
    flex-direction: column;
    color: white;
    justify-content: space-between;
}

.list {
    height: 70vh;
    background-color: rgba(0, 0, 0, 0.5);
    padding: 16px;
    border-radius: 16px;
}

#local {
    color: #b48354;
    font-style: italic;
    font-weight: bold;
}
</style>  

