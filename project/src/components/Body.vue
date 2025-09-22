<script setup lang="ts">
import { ref } from 'vue'
import Dropdwn from './Dropdwn.vue';
import ContactCard from './ContactCard.vue';

let isLoading = ref(true)
let usersLi = ref(null);
const selectedRec = ref('');

//function to set 'selectedRc'
//in here I have to change selectedRec to an object with
//all the users info instead of just a selectedRec var with a name
//then I can pass users info to child components
const getSelectedVal = (value) => {
  selectedRec.value = value;
}

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
    <ContactCard :usersLi="usersLi"
    :userName="selectedRec"/>
    
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
