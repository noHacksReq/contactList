<script setup lang="ts">
import { ref } from 'vue';

let selectedUser = ref(null);
const props = defineProps({
  usersLi: Array
})


const emit = defineEmits(['selected']);

const trigger = () => {
   emit('selected', selectedUser.value)
}

</script>

<template>

    <div>
      
        <form class="dropCont">
    <div >
      <div>
        <label for="contacts">Choose a contact</label>
      </div>
      
      <select name="contacts" id="contacts"
      v-model="selectedUser"
      @change="trigger">
        <option disabled value="">Choose User</option>
        <option
        v-for="userName in usersLi"
        >{{ userName.name }}</option>
        <option>One</option>
        <option>Two</option>
        <option>Three</option>
      </select>
    </div>
    </form>
    </div>
</template>

<style scoped>

</style>