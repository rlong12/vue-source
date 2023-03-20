<script setup>
import Deep from './Deep.vue'
</script>

<template>
    <div>
        <h2>This is the Middle Component. First Child. There are no props in this Component. It imports the Deep Component</h2>
        <section>
            <Deep></Deep>
        </section>
    </div>
</template>

<style scoped>
div {
    background-color: blue;
    display: flex;
    flex-direction: column;
    align-items: center;
}
</style>