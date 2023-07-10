<template>
    <div class="wrapper">
        <div class="browse">
            <div class="user">
                <RouterLink to="/"><h1>user</h1></RouterLink>
            </div>
            <div class="filesystem">
                <div v-for="file in fileList" class="catalog">
                    <img class="icon" :src="icon"/>
                    <p class="name">{{file}}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { RouterLink } from 'vue-router'
import axios from 'axios'

export default {
    name: 'BrowseView',
    mounted() {
        document.body.style.backgroundImage = `url(${this.background})`;
    },
    methods: {
        getCatalogs(): string[] | void {
            axios.get('./mockFile.json').then((response: any) => {
                let dirs: string[] = [];
                for (let i = 0; i < response.data.catalogs.length; i++) {
                    dirs.push(response.data.catalogs[i].name);
                }
                return dirs;
            });
        }
    },
    computed: {
        background(): string {
            return "https://source.unsplash.com/random/1920x1080";
        },
        icon(): string {
            return "https://cdn-icons-png.flaticon.com/512/5994/5994710.png"
        },
        fileList(): string[] {
            return ["home", "user", "folder", "dir"];
        }
    },
}
</script>

<style>
.wrapper {
    height: 100%;
    background-color: rgba(0,0,0,0.5);
}

.browse {
    display: flex;
    flex-direction: column;
    color: white;
    justify-content: space-between;
}

.toolbar {
    width: 100vw;
    margin: 0;
    background-color: rgba(0, 0, 0, 0.5);
}

.user, .filesystem {
}

.toolbar {
}

.icon {
    width: 32px;
    height: 32px;
    padding: 0;
    margin: 0;
}

.name {
    padding: 0;
    margin: 0;
}

.catalog {
}
</style>  

