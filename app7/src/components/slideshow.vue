<script setup>
    import { ref, reactive } from 'vue'
    import { createClient } from 'pexels'
    import { watch } from 'vue'
    import { onMounted } from 'vue'

    //const client = createClient('cwBJxnVW4O78Q4L7lXqPvccxeeOTf6601Nx2pvocOcC2srfL48ixOhhQ')

    // const collection = reactive({
    //     media: {},
    // })

    const collection = [
        {
            name: "Skiing",
            photographer: "Visit Almaty",
            photographer_url: "https://www.pexels.com/@visitalmaty/",
            url: "../.././skiing-pic.jpg"
        },
        {
            name: "Basketball dunk",
            photographer: "Wallace Chuch",
            photographer_url: "https://www.pexels.com/@chuck/",
            url: "../.././basketball-pic.jpg"
        },
        {
            name: "Baseball field",
            photographer: "Pixabay",
            photographer_url: "https://www.pexels.com/@pixabay/",
            url: "../.././baseball-pic.jpg"
        },
        {
            name: "Football",
            photographer: "football wife",
            photographer_url: "https://www.pexels.com/@football-wife-577822/",
            url: "../.././football-pic.jpg"
        },
        {
            name: "Soccer ball",
            photographer: "Pixabay",
            photographer_url: "https://www.pexels.com/@pixabay/",
            url: "../.././soccer-pic.jpg"
        },
        {
            name: "Swimming",
            photographer: "Guduru Ajay bhargav",
            photographer_url: "https://www.pexels.com/@ajaybhargavguduru/",
            url: "../.././swimming-pic.jpg"
        }
    ] 

    let currentPhoto = ref(0)

    let photo = reactive({
        name: "",
        photographer: "",
        photographer_url: "",
        url: ""
    })

    photo.name = collection[currentPhoto.value].name
    photo.photographer = collection[currentPhoto.value].photographer
    photo.photographer_url = collection[currentPhoto.value].photographer_url
    photo.url = collection[currentPhoto.value].url
    
    // async function getCollection() {
    //     // get the meta-data for all collections
    //     let result = await client.collections.all({ per_page: 1 })

    //     // get the id of first collection
    //     const id = result.collections[0].id

    //     // get media for the collection
    //     result = await client.collections.media({ id, type: 'photos', per_page: 6 })

    //     // cache the media meta-data
    //     collection.media = result.media
    // }

    // async function loadImage() {
    //     let index = 0

    //     photo.title = collection.media[index].alt
    //     photo.photographer = collection.media[index].photographer
    //     photo.photographer_url = collection.media[index].photographer_url
    //     photo.url = collection.media[index].src.tiny
    // }

    // watch(collection, () => {
    //     console.log("collection changed")

    //     if (collection.media.length > 0) {
    //         loadImage()
    //     }
    // })

    // onMounted(() => {
    //     console.log("onmounted")
    //     getCollection()
    // })

    function enableNext () {
        let button = document.getElementById("next")
        button.disabled = false;
    }

    function enablePrev () {
        let button = document.getElementById("previous")
        button.disabled = false;
    }

    function nextPhoto() {
        let compare = collection[4];

        if(JSON.stringify(photo) === JSON.stringify(compare)) {
            currentPhoto.value++;

            photo.name = collection[currentPhoto.value].name
            photo.photographer = collection[currentPhoto.value].photographer
            photo.photographer_url = collection[currentPhoto.value].photographer_url
            photo.url = collection[currentPhoto.value].url

            let button = document.getElementById("next")
            button.disabled = true;
        }
        else {
            currentPhoto.value++;

            photo.name = collection[currentPhoto.value].name
            photo.photographer = collection[currentPhoto.value].photographer
            photo.photographer_url = collection[currentPhoto.value].photographer_url
            photo.url = collection[currentPhoto.value].url        
        }

        enablePrev();
    }

    function prevPhoto() {
        let compare = collection[1];

        if(JSON.stringify(photo) === JSON.stringify(compare)) {
            currentPhoto.value--;

            photo.name = collection[currentPhoto.value].name
            photo.photographer = collection[currentPhoto.value].photographer
            photo.photographer_url = collection[currentPhoto.value].photographer_url
            photo.url = collection[currentPhoto.value].url  
            
            let button = document.getElementById("previous")
            button.disabled = true;
        }
        else {
            currentPhoto.value--;

            photo.name = collection[currentPhoto.value].name
            photo.photographer = collection[currentPhoto.value].photographer
            photo.photographer_url = collection[currentPhoto.value].photographer_url
            photo.url = collection[currentPhoto.value].url  
        }

        enableNext();
    }

</script>

<template>
    <h1>Sports slideshow</h1>
    <img :src="photo.url">
    <p> {{ photo.name }} </p><br>
    <a :href="photo.photographer_url" target="_blank"> {{ photo.photographer }} </a>
    <br>
    <button type="button" id="previous" @click="prevPhoto" disabled>Previous</button>
    <button type="button" id="next" @click="nextPhoto">Next</button>
</template>

<style>
    img {
        scale: .1 ;
    }
    /* img {
        scale: .2;
        position: relative;
        left: -1400px;
        top: -1000px;
    }

    button {
        position: relative;
        top: -2000px;
        left: 550px;
        margin: 30px;
        padding: 10px;
        width: 100px;
    }
    
    p {
        position: relative;
        top: -2050px;
        left: 550px;
        font-size: 40px;
    } */
</style>