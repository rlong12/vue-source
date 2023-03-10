<script setup>
import { ref, reactive } from 'vue'
import Child from './Child.vue'
import Card from './Card.vue'

let arr = reactive([])
const cardInfo = ref({})

</script>

<template>
    <div>
        <Child
        v-model:info="cardInfo"
        @addCard="() => arr.push({...cardInfo})" />
    </div>
    <div>
        <section v-for="elm in arr">
            <Card :name="elm.name" :color="elm.color" />
        </section>
    </div>
</template>

<style scoped></style>