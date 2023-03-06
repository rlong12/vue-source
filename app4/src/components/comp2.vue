<script setup>
    import {ref} from 'vue'

    const p1 = ref("Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Commodo odio aenean sed adipiscing diam donec adipiscing tristique risus. Sed blandit libero volutpat sed cras ornare. Scelerisque viverra mauris in aliquam sem fringilla ut morbi. Nulla facilisi nullam vehicula ipsum a arcu cursus vitae congue. Varius morbi enim nunc faucibus a pellentesque sit amet. Purus sit amet volutpat consequat. Odio pellentesque diam volutpat commodo sed egestas egestas fringilla phasellus. Sem viverra aliquet eget sit amet tellus. Metus vulputate eu scelerisque felis imperdiet proin fermentum leo. Molestie at elementum eu facilisis sed odio. Auctor augue mauris augue neque gravida in fermentum et. Donec pretium vulputate sapien nec sagittis aliquam malesuada bibendum arcu. Hendrerit dolor magna eget est lorem ipsum dolor sit amet. Risus nec feugiat in fermentum posuere urna. Venenatis tellus in metus vulputate.")
    const p2 = ref("Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Consectetur adipiscing elit duis tristique sollicitudin. Adipiscing commodo elit at imperdiet dui accumsan sit amet nulla. Sit amet tellus cras adipiscing enim. Molestie nunc non blandit massa enim nec dui nunc. Vestibulum sed arcu non odio euismod lacinia at quis. Facilisi nullam vehicula ipsum a arcu cursus vitae congue. Nunc sed velit dignissim sodales ut eu sem integer. Aliquam ut porttitor leo a. Ultrices mi tempus imperdiet nulla malesuada pellentesque elit eget gravida. Vel orci porta non pulvinar neque laoreet suspendisse. Id faucibus nisl tincidunt eget nullam. Lectus magna fringilla urna porttitor rhoncus dolor purus. Dolor sit amet consectetur adipiscing elit pellentesque.")
    const p3 = ref("Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Bibendum est ultricies integer quis auctor elit sed vulputate mi. Pulvinar pellentesque habitant morbi tristique senectus et. Bibendum arcu vitae elementum curabitur vitae nunc sed velit dignissim. Tellus in hac habitasse platea dictumst vestibulum rhoncus. Eros in cursus turpis massa. Quis viverra nibh cras pulvinar mattis nunc sed blandit libero. Pellentesque dignissim enim sit amet venenatis urna cursus. Nulla porttitor massa id neque aliquam vestibulum morbi blandit. Magna fringilla urna porttitor rhoncus dolor purus non enim. Fames ac turpis egestas sed tempus urna et pharetra. At tempor commodo ullamcorper a lacus. Sed libero enim sed faucibus turpis in eu. Enim neque volutpat ac tincidunt vitae semper quis lectus nulla. Sociis natoque penatibus et magnis dis parturient montes nascetur. Id diam vel quam elementum pulvinar etiam non. Nec tincidunt praesent semper feugiat nibh sed pulvinar proin. Quam quisque id diam vel quam elementum pulvinar etiam non. Morbi tristique senectus et netus et malesuada fames. Turpis egestas maecenas pharetra convallis posuere morbi leo urna molestie.")
    const textColor = ref("purple")

    function changeText() {
        textColor.value = (textColor.value == 'purple') ? "green" : "purple"
    }

</script>

<template>
    <p :class="textColor">
    {{ p1 }} <br><br>
    {{ p2 }} <br><br>
    {{ p3 }} <br><br>
    </p>

  <button @click="changeText()">Change Text</button>

</template>

<style>
    .purple {
        color: purple
    }

    .green {
        color: green
    }

</style>