<template>
    <app-content>
        <template v-slot:nav>
            <ul>
                <li v-for="item in questions" :key="item.id"
                    :class="{ active: item.id === selectedQuestionId }"
                    @click="questionHandler(item.id)">
                    <a>{{ item.name }}</a>
                </li>
            </ul>
        </template>
        <template v-slot:info>{{ selectedQuestion.content }}</template>
    </app-content>
</template>

<script>
    import AppContent from './shared/Content';

    export default {
        components: {
            AppContent
        },
        props: {
            questions: {
                type: Array,
                required: true
            }
        },
        data() {
            return {
                selectedQuestionId: 1
            }
        },
        methods: {
            questionHandler(id) {
                this.selectedQuestionId = id;
            }
        },
        computed: {
            selectedQuestion() {
                return this.questions.find(q => q.id === this.selectedQuestionId);
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
