<script>
    export default {
        // Add code if/as necessary
        // Hint: Add properties subject, entry and mood
        data() {
            return {
                
            }
        },

        props: {
            postList: Array,
        },

        methods: {
            moodToLink (mood) {
                return `/assets/${mood.toLowerCase()}.png`
            }
        }
    };
</script>


<template>
    <!-- TODO: add your template code here. Use boostrap card -->
    <div v-for="post in postList" :key="post.id">
        <div class="card" style="width:18rem">
            <img class="card-img-top" :src="moodToLink(post.mood)" alt="Card image">
            <div class="card-body">
                <h5 class="card-title">{{post.subject}}</h5>
                <p class="card-text">{{post.entry}}</p>
            </div>
        </div>
    </div>
</template>