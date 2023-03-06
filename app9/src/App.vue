<script setup>
    import { ref, reactive } from 'vue';
    import AnimalSounds from './components/AnimalSounds.vue';
    import { sounds } from './assets/audios.js'  

</script>

<template>
    <ul id="outer">
        <li v-for="elm in sounds">
            <AnimalSounds 
                :title="elm.title" :duration="elm.duration" :url="elm.url" />

        </li>
    </ul>
</template>
<style scoped>
    #outer {
        display: flex;
        flex-direction: column;
    }

    li {
        display: flex;
        align-items: center;
    }
</style>
