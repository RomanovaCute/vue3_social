<template>
    <form @submit.prevent>
        <h3>Создайте свой пост</h3>
        <input 
            v-model="post.title"
            class="input" 
            type="text" 
            placeholder="Название"/>
        <input 
            v-model="post.body"
            class="input" 
            type="text" 
            placeholder="Описание"/>
        <button 
            class="btn"
            @click="createPost"
        >
            Создать
        </button>
    </form>
</template>

<script>
    export default {
        data() {
            return {
                post: {
                    title: "",
                    body: ''
                }
            }
        },
        methods: {
            createPost() {
                this.post.id = Date.now();
                this.$emit('create', this.post, 'second param', '3 param') // emit позволяет передавать значения из дочернего компонента в родительский, create(post) - генерируем событие, post - аргумент, пост, который создается
                this.post = {
                    title: '',
                    body: ''
                }
            }
        }
    }
</script>

<style>
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