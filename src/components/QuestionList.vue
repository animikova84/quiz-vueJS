<template>
    <div class="question-list">
        <h1>{{ title }}</h1>
        <Question v-for="q in questions" :key="q.id" :title="q.title" :answers="q.answers" />
    </div>
</template>

<script>
    import Question from "./Question";

    export default {
        name: 'QuestionList',
        components: {Question},
        props:['questions'],
        data: function() {
            return {
                title: 'Quiz 1'
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
