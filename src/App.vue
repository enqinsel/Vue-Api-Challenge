<script setup>
import { onMounted, ref } from 'vue';
import Image from "./components/Image.vue"
import ButtonComp from './components/ButtonComp.vue';

const data = ref([])
const image = ref([])

async function fetchData() {
  const result = await fetch("https://dog.ceo/api/breeds/list/all")
    .then(data => data.json())
    .then(response => Object.keys(response.message))

  return result
}

async function fetchImagesData(name) {
  const result = await fetch(`https://dog.ceo/api/breed/${name}/images`)
    .then(data => data.json())
    .then(response => response.message)

  return result
}


const selectHandler = async (dogs) => {
  image.value = await fetchImagesData(dogs)
}


onMounted(async () => {
  data.value = await fetchData()
})


</script>

<template>
  <main>
    <div class="buttons">
      <ButtonComp v-for="dogs in data" :name="dogs" @dogs="selectHandler(dogs)">
      </ButtonComp>
    </div>
    <div class="image">
      <Image v-for="img in image" :url="img"> </Image>
    </div>
  </main>
</template>

<style scoped>

main{
  width: auto;
  height: auto;
  background-color: rgba(179, 13, 13, 0.286);
}

</style>
