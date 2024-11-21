<template>
    <div>
        
        <h1> 
            Page ranking
        </h1>

        <table border="1">
            <tr>
                <th> Position </th>
                <th> Artist </th>
                <th> Votes </th>
            </tr>

            <tr v-for="(rankingItem, index) in ranking" :key="index">
                <td>
                    {{ index + 1 }}
                </td>
                <td>
                    {{  rankingItem.artist_name }} - {{ rankingItem.song_name }}
                </td>
                <td>
                    {{  rankingItem.total_points }}
                </td>
            </tr>
        </table>
    </div>
</template>

<script>
    export default {
        name: 'PageRanking',
        mounted() {
            this.fetchRanking();
        },
        data() {
            return {
                ranking: []
            }
        },
        methods: {
            fetchRanking() {
                fetch("http://localhost:3000/api/ranking")
                    .then(response => response.json())
                    .then(data => {
                        console.log(data);
                        this.ranking = data;
                    })
            }
        }
    }
</script>