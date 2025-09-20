<script setup lang="ts">
import { ref } from 'vue';

let selected = ref('');

defineExpose(selected)

</script>

<template>
    <div>
        <form class="dropCont">
    <div >
      <div>
        <label for="contacts">Choose a contact</label>
      </div>
      
      <select name="contacts" id="contacts"
      v-model="selected">
        <option disabled value="">Choose User</option>
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