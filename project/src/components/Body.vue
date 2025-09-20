<script setup lang="ts">
import { ref, useTemplateRef } from 'vue'
import Dropdwn from './Dropdwn.vue';

const selectedRef = useTemplateRef('selected');

let usersLi = ref(null);
//let props = defineProps([]);

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



<template ref="selected">
  <div class="bodyCont">
    <Dropdwn ref="selected"
    :usersLi="usersLi"
    />
    <div>
      <h3>Contact Info</h3>
      <p>{{ selectedRef }}</p>
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
