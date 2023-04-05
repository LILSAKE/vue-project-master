<template>
    <div>
        post id: {{ $router.currentRoute.params.id }}
    </div>
</template>

<script>
import axios from 'axios';
// import { threadId } from 'worker_threads';

export default {
    name: 'PostPage',
    data(){
        return {
            post: {},
        }
    },
    methods: {
        async getPost(postId){
            try {
                const response = await axios.get(`https://jsonplaceholder.typicode.com/posts/${postId}`)
                this.post = response.data
                console.log(this.post)
            }
            catch(error){
                console.error(error)
            }
        },
    },
    created() {
        this.getPost(this.$router.currentRoute.params.id)
    },
}
</script>

<style>

</style>