<template>
    <div class="app">
        <div>
            <form @submit.prevent>
                <h3>Создайте свой пост</h3>
                <input 
                    v-bind:value="title"
                    @input="title = $event.target.value"
                    class="input" 
                    type="text" 
                    placeholder="Название"/>
                <input 
                    v-bind:value="body" 
                    @input="body = $event.target.value"
                    class="input" 
                    type="text" 
                    placeholder="Описание"/>
                <button class="btn" @click="creatPost">Создать</button>
            </form>
        </div>
        <div class="post" v-for="post in posts" v-bind:key="post.id">
            <div><strong>Название:</strong> {{ post.title }}</div>
            <div><strong>Описание:</strong> {{ post.body }}</div>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                posts: [
                    {id: 1, title:'JavaScript', body: 'Описание поста'},
                    {id: 2, title:'JavaScript 2', body: 'Описание поста 2'},
                    {id: 3, title:'JavaScript 3', body: 'Описание поста 3'},
                ],
                title: '',
                body: ''
            }
        },
        methods: {
            creatPost() {
                const newPost = {
                    id: Date.now(),
                    title: this.title,
                    body: this.body
                }
                this.posts.push(newPost)
                this.title = ''
                this.body = ''
            },
            // inputTitle(event){
            //     this.title = event.target.value
            // }
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

    .post {
        padding: 15px;
        border: 2px solid teal;
        border-radius: 12px;
        margin-top: 15px;
        padding: 10px 15px;
        background: rgb(188, 213, 209);
    }
    .input {
        width: 100%;
        border: 1px solid teal;
        padding: 10px 15px;
        margin-top: 15px;
        border-radius: 7px;
    }
    form {
        display: flex;
        flex-direction: column;
    }
    .btn {
        align-self: flex-end;
        margin-top: 15px;
        padding: 10px 15px;
        color: teal;
        border: 2px solid teal;
        background: none;
    }
</style>