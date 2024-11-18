<template>
    <div>
        <h1>
            Artists
        </h1>
        
        <ul>
            <li v-for="(artist, index) in artists" :key="index">
                {{ artist.name }}
            </li>
        </ul>

        <hr>

        <label> Artist </label>
        <input type="text">
        <button> 
            Add artists
        </button>
    </div>
</template>

<script>
    export default {
        name: 'PageArtists',
        mounted() {
            this.fetchArtists();
        },
        data() {
            return {
                artists: []
            }
        },
        methods: {
            fetchArtists() {
                fetch("http://localhost:3000/api/artists")
                    .then(response => response.json())
                    .then(data => {
                        this.artists = data;
                    })
            },
            addArtist() {
                console.log("Add artist");
            }
        }
    }
</script>