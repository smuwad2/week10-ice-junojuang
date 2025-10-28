<script setup>
    // Import BlogPost component
    import BlogPost2 from './subcomponents/BlogPost2.vue'
	import axios from 'axios'
</script>

<script>
    export default {
        data() {
            return {
                posts: [] // array of post objects
            }  
        },
        components:{
            BlogPost2
        }, 

        computed: {
            baseUrl() {
                if (window.location.hostname == 'localhost')
                    return 'http://localhost:3000'
                else {
                    const codespace_host = window.location.hostname.replace('5173', '3000')
                    return `https://${codespace_host}`;
                }
            }
        },
        created() { // created is a hook that executes as soon as Vue instance is created
            axios.get(`${this.baseUrl}/posts`)
            .then(response => {
                // this gets the data, which is an array
                this.posts = response.data
                console.log(response.data)
            })
            .catch(error => {
                this.posts = [{ entry: 'There was an error: ' + error.message }]
            })
        },
        methods: {
            deletePost(id) {
                // TODO: Complete the delete method
                try{
                axios.get(`${this.baseUrl}/deletePost`, {params:{id}})
                this.posts = this.posts.filter(p => p.id !== id) 
                }catch(e){
                    console.error(e)
                    alert('Failed to delete')
                }

                

            }
        }
    }
</script>

<template>
   <!-- TODO: make use of the 'blog-post' component to display the blog posts -->
    <BlogPost2 v-for="post in posts" :mood="post.mood" :entry="post.entry"><button @click="deletePost(post.id)">Delete</button></BlogPost2>
</template>

