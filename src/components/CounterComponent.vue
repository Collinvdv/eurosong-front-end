<template>
    <div>
        <h2>
            {{ nummertje }}
        </h2>

        <button @click="plusOne()" v-if="this.nummertje < 10">
            +
        </button>
        <button @click="minusOne()" v-if="this.nummertje > 0">
            -
        </button>
    </div>
</template>

<script>
    export default {
        name: 'CounterComponent',
        props: ["initialValue"],
        mounted() {
            this.nummertje = parseInt(this.initialValue);
        },
        data() {
            return {
                nummertje: 1
            }
        },
        methods: {
            plusOne() {
                if (this.nummertje < 10) {
                    this.nummertje++;
                }
            },
            minusOne() {
                if (this.nummertje > 0) {
                    this.nummertje--;
                }
            }
        }
    }
</script>