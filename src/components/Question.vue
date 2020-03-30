<template>
    <div class="question">
        <h2>{{title}}</h2>
        <ul>
            <li v-for="(answer, i) in answers" :key="i">{{ answer }}</li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: 'Question',
        props: {
            id: Number,
            title: String,
            answers: Array
        },
        data: function() {
            return {

            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
