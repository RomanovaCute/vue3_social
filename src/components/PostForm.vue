<template>
    <form @submit.prevent>
        <h3>Создайте свой пост</h3>
        <input 
            v-bind:value="post.title"
            @input="post.title = $event.target.value"
            class="input" 
            type="text" 
            placeholder="Название"/>
        <input 
            v-bind:value="post.body" 
            @input="post.body = $event.target.value"
            class="input" 
            type="text" 
            placeholder="Описание"/>
        <button 
            class="btn"
            >Создать
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