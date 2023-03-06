<script setup>
import { onMounted, ref } from 'vue'
 

const audio = ref(null);

const props = defineProps({
    title: String,
    duration: String,
    url: String
})

function getAudio() {
    console.log("setting audio")
    return new URL(`../assets/animal-sounds-folder/${props.url}`, import.meta.url)

}

onMounted(() => {
    audio.value.src = getAudio()
})

</script>

<template>
    <section>
            <p>{{ props.title }} {{ props.duration }}</p>
            <audio ref="audio" controls></audio><br>
    </section>
</template>

<style>
p {
        font-size: 20px;
    }
</style>