<template>
    <div class="mdl-grid">
        <topic
                v-for="topic in topics"
                v-bind:key="topic.id"
                v-bind:topic="topic"
                v-on:topic-selected="onTopicSelected($event)"
        ></topic>
    </div>
</template>

<script>
    import Topic from './Topic.vue'
    import { EventBus } from '../main.js';

    export default {
        name: "topics-list",
        props: ['topics'],
        data: function () {
            return {
                selectedTopic: null
            };
        },
        methods: {
            onTopicSelected: function(topic) {
                EventBus.$emit('topic-selected', topic);
            }
        },
        components: {
            Topic
        }
    }
</script>

<style scoped>

</style>