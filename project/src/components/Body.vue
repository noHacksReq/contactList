<script setup lang="ts">
import { ref } from 'vue'
import Dropdwn from './Dropdwn.vue';
import ContactCard from './ContactCard.vue';

let isLoading = ref(true)
let usersLi = ref(null);
const selectedRec = ref('');
const selectedIndex = ref(null);
let currentUser = ref({});


const getSelectedVal = (value, getIndex) => {
  selectedRec.value = value;
  selectedIndex.value = getIndex;
  currentUser.value = usersLi.value[getIndex];
  
  return currentUser
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
    usersLi.value = data
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
      <div v-else>
        <Dropdwn 
    @selected="getSelectedVal"
    :usersLi="usersLi"
    />
    <ContactCard 
    :selectedUser="currentUser"
    
    />
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
