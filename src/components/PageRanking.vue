<template>
    <div>
        Page ranking
    </div>
</template>

<script>
    export default {
        name: 'PageRanking',
        mounted() {
            this.fetchRanking();
        },
        methods: {
            fetchRanking() {
                fetch("http://localhost:3000/api/ranking")
                    .then(response => response.json())
                    .then(data => {
                        console.log(data);
                    })
            }
        }
    }
</script>