<script setup>
    import { inject } from 'vue';

    const message = inject('message')
</script>

<template>
    <div>
        <h3>This is the Deep Component. The message from the Parent is injected here and displayed. No props used.</h3>
        <p>{{ message }}</p>
    </div>
</template>

<style scoped>
div {
    background-color: blueviolet;
    display: flex;
    flex-direction: column;
    align-items: center;
}
</style>