<script setup>
const props = defineProps(["name"])
const emits = defineEmits(["dogs"])

const clickHandler = () => {
    emits("dogs")
}
</script>

<template>
    <button class="dogs" @click="clickHandler">{{props.name}}</button>
</template>


<style scoped>

.dogs {
  width: 150px;
  height: auto;
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  align-content: flex-start;
  justify-content: flex-start;
  align-items: flex-start;
  background-color: rgba(191, 255, 0, 0.636);
  float: left;
}

.dogs:hover{
    cursor: pointer;
}

</style>