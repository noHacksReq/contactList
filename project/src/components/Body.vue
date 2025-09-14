<script setup lang="ts">
import { ref } from 'vue'

let selected = ref(null)

</script>



<template>
  <div class="bodyCont">
    <form class="dropCont">
    <div >
      <div>
        <label for="contacts">Choose a contact</label>
      </div>
      
      <select name="contacts" id="contacts"
      v-model="selected">
        <option value="one">One</option>
        <option value="two">Two</option>
        <option value="three">Three</option>
      </select>
    </div>
    </form>
    <div>
      <h3>Contact Info</h3>
      <p>{{ selected }}</p>
    </div>
  </div>
</template>

<style scoped>

.bodyCont {
  display: flex;
  flex-direction: column;
}

form {
  display: flex;
  flex-direction: column;
}

</style>
