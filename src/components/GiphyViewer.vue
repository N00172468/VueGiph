<template>
    <div>
        <div class="search-box">
            <input type="text" v-model="term" v-on:keyup.enter="searchGiphy()" />
            <b-button class="float-right" variant="primary" @click="searchGiphy()">Search</b-button>
        </div>

        <b-card-group columns>
            <b-card
                v-for="gif in gifs"
                :key="gif.id"
                :img-src="gif.images.fixed_width.url"
                :img-alt="gif.title">
                <b-card-text>
                    <a href="gif.url" target="_blank">{{ gif.title }}</a>
                </b-card-text>
            </b-card>
        </b-card-group>
    </div>
</template>

<script>
/* eslint-disable no-console */
import axios from 'axios'

const GIPHY_URL = "https://api.giphy.com/v1/gifs";
const API_KEY = "c5uhkIh6od7M07RcwDFKiT7tzdTB5CEB";

export default {
    name: "GiphyViewer",
    components: {

    },
    data() {
        return {
            gifs: []
        };
    },
    mounted() {
        axios.get(`${GIPHY_URL}/trending?api_key=${API_KEY}`)
        .then(response => (
            this.gifs = response.data.data
        ))
        .catch(error => console.log(error))
    },
    methods: {
        searchGiphy() {
            if (!this.term) {
                alert("Enter the search term s'il vous plait!");
                return;
            }
            axios.get(`${GIPHY_URL}/search?api_key=${API_KEY}&q={this.term}&limit=20`)
            .then(response => (
                this.gifs = response.data.data
            ))
            .catch(error => console.log(error))
            
            this.term = ""
        }
    }
};
</script>

<style>
.search-box {
    margin-top: 20px;
    margin-bottom: 20px;
}
</style>