<script setup lang="ts">
import { ref } from 'vue'

let selected = ref('');
let usersLi = ref('');

function getUsers() {
  fetch('https://jsonplaceholder.typicode.com/users')
  .then(response => {
    if (!response.ok) {
      throw new Error(`HTTP error! Status: ${response.status}`);
    }
    return response.json(); // Parse the response body as JSON
  })
  .then(data => {
    usersLi = data
   // console.log(users); // Log the parsed JSON data
  })
  .catch(error => {
    console.error('Error fetching data:', error); // Handle any errors during the fetch operation
  });
}
getUsers()




console.log(usersLi.value)
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
        <option disabled value="">Choose User</option>
        <option>One</option>
        <option>Two</option>
        <option>Three</option>
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
