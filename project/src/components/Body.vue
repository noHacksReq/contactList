<script setup lang="ts">
import { ref } from 'vue'
import Dropdwn from './Dropdwn.vue';

let isLoading = ref(true)
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
    isLoading.value = false;
   
  })
  .catch(error => {
    console.error('Error fetching data:', error); // Handle any errors during the fetch operation
  });
}
getUsers()

</script>



<template ref="selected" >
  <div class="bodyCont">
    <div v-if="isLoading" 
      class="loading">LOADING</div>
    <Dropdwn v-else
    @selected="getSelectedVal"
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
