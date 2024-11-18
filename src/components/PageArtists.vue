<template>
    <div>
        Page artists
    </div>
</template>

<script>
    export default {
        name: 'PageArtists',
        mounted() {
            fetch("http://localhost:3000/api/artists")
                .then(response => response.json())
                .then(artists => {
                    console.log(artists);
                })
        }
    }
</script>