<script setup>
    import {ref} from 'vue'

    const title = ref("App 4")
    const imageSrc = ref("Dr.Mcgregor.png")
</script>

<template>
    <h1> {{ title }} </h1>
    <img :src="imageSrc"/>
</template>

<style>
</style>