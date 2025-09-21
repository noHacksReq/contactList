<script setup lang="ts">
import { ref } from 'vue'
import Dropdwn from './Dropdwn.vue';

//ref to recieve value from 'selected' emit in dropdown
const selectedRec = ref('');

//function to set 'selectedRc'
const getSelectedVal = (value) => {
  selectedRec.value = value;
  
}

let usersLi = ref(null);

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
   
  })
  .catch(error => {
    console.error('Error fetching data:', error); // Handle any errors during the fetch operation
  });
}
getUsers()

</script>



<template ref="selected" >
  <div class="bodyCont">
    <Dropdwn @selected="getSelectedVal"
    :usersLi="usersLi"
    />
    <div>
      <h3>Contact Info</h3>
      <p>{{ selectedRec }}</p>
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
