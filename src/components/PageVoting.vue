<template>
    <div>
        <h1>
            Page Voting
        </h1>
        
        <div>
            <button @click="prevSong()" :disabled="activeSongIndex == 0">
                Prev song
            </button>
            
            <div v-if="songs.length > 0">
                {{ songs[activeSongIndex].artist_name }} - Song {{ songs[activeSongIndex].song_name }}
            </div>
            <button @click="nextSong()" :disabled="activeSongIndex == songs.length - 1">
                Next song
            </button>
        </div>

        <hr>
        <div>
            <button @click="addVote(2)" :disabled="this.votesSended.includes(2)"> Add 2 votes</button>
            <button @click="addVote(4)" :disabled="this.votesSended.includes(4)"> Add 4 votes</button>
            <button @click="addVote(6)" :disabled="this.votesSended.includes(6)"> Add 6 votes</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'PageVoting',
        mounted() {
            this.fetchSongs();
        },
        data() {
            return {
                songs: [],
                votesSended: [],
                activeSongIndex: 0
            }
        },
        methods: {
            addVote(points) {
                fetch("http://localhost:3000/api/votes", {
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json"
                    },
                    body: JSON.stringify({
                        song_id: this.songs[this.activeSongIndex].song_id,
                        points: points
                    })
                })
                    .then(response => response.json())
                    .then(() => {
                        this.votesSended.push(points);

                        if (this.votesSended.length == 3) {
                            this.$emit('cp', 'ranking');
                        }

                    })
            },
            fetchSongs() {
                fetch("http://localhost:3000/api/songs")
                    .then(response => response.json())
                    .then(data => {
                        this.songs = data;
                    })
            },
            prevSong() {
                if (this.activeSongIndex > 0) {
                    this.activeSongIndex--;
                }
            },
            nextSong() {
                if (this.activeSongIndex < this.songs.length - 1) {
                    this.activeSongIndex++;
                }
            },
        }
    }
</script>