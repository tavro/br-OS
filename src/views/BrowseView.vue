<template>
    <div class="wrapper">
        <div class="browse">
            <div class="user">
                <RouterLink to="/"><h1>user</h1></RouterLink>
            </div>
            <div class="filesystem">
                <div v-for="catalog in catalogs" class="catalog">
                    <img class="icon" :src="folderIcon"/>
                    <p class="name">{{catalog}}</p>
                </div>
                <div v-for="file in files" class="file">
                    <img class="icon" :src="fileIcon"/>
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
        axios.get('./mockFile.json').then((response: any) => {
            let dirs: string[] = [];
            let files: string[] = [];
            for (let i = 0; i < response.data.catalogs.length; i++) {
                dirs.push(response.data.catalogs[i].name);
            }
            for (let i = 0; i < response.data.files.length; i++) {
                files.push(response.data.files[i].name);
            }
            this.files = files;
            this.catalogs = dirs;
        });
    },
    data() {
        return {
            catalogs: [] as string[],
            files: [] as string[],
        }
    },
    methods: {
    },
    computed: {
        background(): string {
            return "https://source.unsplash.com/random/1920x1080";
        },
        folderIcon(): string {
            return "https://cdn-icons-png.flaticon.com/512/5994/5994710.png"
        },
        fileIcon(): string {
            return "https://freesvg.org/img/Anonymous_Paper_2_icon.png"
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

