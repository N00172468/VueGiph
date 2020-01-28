<template>
    <div>
        Tis a GiphyViewer Component
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

    }
};
</script>