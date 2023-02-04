<template>
    <form @submit.prevent>
        <h3>Создайте свой пост</h3>
        <my-input 
            v-model="post.title"
            type="text"
            placeholder="Название"/>
        <my-input 
            v-model="post.body"
            type="text"
            placeholder="Описание"/>
        <my-button 
            class="btn"
            style="align-self: flex-end"
            @click="createPost"
        >
            Создать
        </my-button>
    </form>
</template>

<script>
import MyButton from '@/components/UI/MyButton.vue';
    export default {
        components: {
            MyButton
        },
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
    form {
        display: flex;
        flex-direction: column;
    }
</style>