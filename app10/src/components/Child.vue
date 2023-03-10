<script setup>
import { ref, computed } from 'vue'

const props = defineProps(['info'])
defineEmits(['updateCard', 'addCard'])

// const info = ref({
//     name: "",
//     color: ""
// })

const value = computed({
    get() { return props.info },
    set(arg) { emit('updateCard', arg) }
})

</script>

<template>
    <div class="outerDiv">
        <div class="innerDiv">
            <h1>Please enter your name and favorite color:</h1>
        </div>
        <div class="innerDiv">
            <form>
                <fieldset>
                    <div>
                        <label for="name">Name</label>
                        <input type="text" id="name" v-model="value.name" />
                    </div>
                    <br>
                    <div>
                        <label for="color">Color</label>
                        <input type="text" id="color" v-model="value.color" />
                    </div>
                    <div>
                        <button @click="$emit('addCard')" type="button">Submit</button>
                    </div>
                </fieldset>
            </form>
        </div>
    </div>
</template>

<style scoped>
.outerDiv {
    border-radius: 20px;
    border: solid 1px lightgray;
}
.innerDiv {
    display: flex;
    flex-direction: column;
    padding: 30px;
}
div {
    display: flex;
    flex-direction: column;
}
button {
    width: 100px;
    height: 30px;
    margin-top: 20px
}
</style>