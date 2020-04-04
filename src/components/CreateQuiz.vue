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
        <template v-slot:info>
            <div class="form-group">
                <input placeholder="Question name..." type="text" id="question" v-model="question" />
            </div>
            <vue-editor v-model="content" />
            <select name="quizes" id="quizes" v-model="questionId">
                <option :value="null" selected>Select a quiz...</option>
                <option v-for="t in quizes" :key="t.id" :value="t.id">{{t.name}}</option>
            </select>
            <button class="btn" @click="createQuestionHandler">Create</button>
            <h3>Content preview</h3>
            <div class="content-preview"></div>
        </template>
    </app-content>
</template>

<script>
    import AppContent from './shared/Content';
    import { VueEditor } from "vue2-editor";

    export default {
        components: {
            AppContent,
            VueEditor
        },
        props: {
            questions: {
                type: Array,
                required: true
            },
            quizes: {
                type: Array,
                required: true
            }
        },
        data() {
            return {
                selectedQuestionId: 1,
                content: "<h1>Add Question...</h1>",
                questionId: null,
                question: ''
            }
        },
        methods: {
            questionHandler(id) {
                this.selectedQuestionId = id;
            },
            createQuestionHandler() {
                const { questionId, question, content } = this.$data;
                this.$emit('create', { questionId, question, content });
                this.questionId = null;
                this.question = '';
                this.content = '<h1>Add Question...</h1>';
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
    @import "~vue2-editor/dist/vue2-editor.css";

</style>
