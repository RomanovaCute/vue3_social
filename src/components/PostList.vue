<template>
<!-- при невыполнении v-if список удаляется полностью из DOM дерева,
лучше использовать v-show -->
    <div v-show="posts.length > 0">
        <h3>Список постов</h3>
        <post-item 
            v-for="post in posts" 
            :post="post"
            :key="post.id"
            @remove="$emit('remove', post)"
        />
    </div>
    <h2 v-show="posts.length === 0" style="color: blue">
        Здесь пока нет постов!
    </h2>
</template>

<script>
import PostItem from '@/components/PostItem.vue';
    export default {
        components: {
            PostItem
        },
        props: {
            posts: {
                type: Array,
                required: true
            }
        }
    }
</script>

<style scoped>
    .post {
        padding: 15px;
        border: 2px solid teal;
        border-radius: 12px;
        margin-top: 15px;
        padding: 10px 15px;
        background: rgb(188, 213, 209);
    }   
</style>