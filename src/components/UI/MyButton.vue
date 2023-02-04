<template>
    <button class="btn">
        <slot></slot>
    </button>
</template>

<script>
    export default {
        name: 'my-button'
    }
</script>

<style scoped>
    .btn {
        margin-top: 15px;
        padding: 10px 15px;
        color: teal;
        border: 2px solid teal;
        background: none;
    }
</style>