<template>
    <div>
        <div v-if="posts.length === 0">
            Добавленных постов нет
        </div>
        <div 
            v-for="(post, index) in posts"
            :key="index"
            class="post"
        >
            <div style="display: flex; justify: space-between; align-items: center;">
                <div style="width: 90%;">
                    <h4>Название поста: {{ post.title }}</h4>
                    <p><strong>Содержание поста:</strong> {{ post.body }}</p>
                </div>
                <div>
                    <button 
                        style="border: 1px solid red; color: red;"
                        @click="deletePost(index)"
                    >
                        Удалить
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    name: "PostList",
    props: {
        posts: {
            type: Array,
            default() {
                return []
            },
            require: true,
        },
    },
    methods: {
        deletePost(index) {
            this.$emit("delete-post", index, "1111")
        }
    }
}
</script>

<style>
</style>