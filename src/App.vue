<template>
    <div class="app">
        <h1>Страница с постами</h1>

        <!-- stop = stopPropagation из JS -->
        <my-button
            @click.stop="showDialog"
        >
            Создать
        </my-button>
        <my-dialog v-model:show="dialogVisible">
            <post-form
                @create="createPost"
            />
        </my-dialog>

        <post-list 
            :posts="posts"
            @remove="removePost"
        />
    </div>
</template>

<script>
import PostForm from "@/components/PostForm.vue"
import PostList from "@/components/PostList.vue"
import MyDialog from './components/UI/MyDialog.vue'
import axios from 'axios'

    export default {
        components : {
            PostForm, PostList,
                MyDialog
        },
        data(){
            return {
                posts: [
                    {id: 1, title:'JavaScript', body: 'Описание поста'},
                    {id: 2, title:'JavaScript 2', body: 'Описание поста 2'},
                    {id: 3, title:'JavaScript 3', body: 'Описание поста 3'},
                ],
                dialogVisible: false
            }
        },
        methods: {
            createPost(post) {
                this.posts.push(post)
                this.dialogVisible = false
            },
            removePost(post) {
                this.posts = this.posts.filter(p => p.id !== post.id)
            },
            showDialog() {
                this.dialogVisible = true
            }
        }
    }
</script>

<style>
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    .app {
        padding: 20px;
    }
</style>