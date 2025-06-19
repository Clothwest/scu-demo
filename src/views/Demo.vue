<script setup>
import { useRoute, useRouter } from "vue-router";
import demoComponent from "../components/demoComponent.vue"
import { ref } from "vue";
import axios from "axios";

const a = 4
const demoComponentName = ref("component")
const demoComponentAction = ref("action")

const route = useRoute()
const router = useRouter()

const change = (name, action) => {
  demoComponentName.value = name
  demoComponentAction.value = action
}
const loadUser = () => {
  axios.get('/api/data', {
    params: {
      name: demoComponentName.value,
      action: demoComponentAction.value
    }
  })
}
</script>

<template>
  <div>
    {{a}}
    {{route.query.id}}
    <demo-component @buttonClicked="change" :name="demoComponentName" :action="demoComponentAction" />
    <button @click="loadUser">log in</button>
  </div>
</template>

<style scoped>

</style>