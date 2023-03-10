<script setup>

    const props = defineProps({
        name: String,
        color: String
    })
</script>

<template>
    <section>
        <p> {{ props.name }} </p>
        <p> {{ props.color }}</p>
    </section>
</template>

<style scoped>
    section {
        margin: 20px;
        background-color: lightgreen;
        width: 150px;
        height: 150px;

        border-radius: 10px;

        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    p {
        font-size: 25px;
        font-family: Georgia, 'Times New Roman', Times, serif;
    }
   
</style>