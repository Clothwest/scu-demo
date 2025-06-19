<script setup>
import { ref } from "vue";

defineProps({
  name: {
    type: String,
    default: "null"
  },
  action: {
    type: String,
    default: "null"
  }
})
const emit = defineEmits(["buttonClicked"])

const message = ref("message")

const clicked = () => {
  emit("buttonClicked","a new name", "I want a new name")
  console.log(message.value)
}
</script>

<template>
<div>
  <h1>demoComponent</h1>
  {{name}}<br/>
  {{action}}<br/>
  <button @click="clicked">button</button><br/>
  <input v-model="message" /><br/>
  {{message}}
</div>
</template>

<style scoped>

</style>