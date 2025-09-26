<script setup lang="ts">
import { ref } from 'vue';

let selectedUser = ref(null);
let userIndex = ref()
const props = defineProps({
  usersLi: Array,
  
});


const emit = defineEmits(['selected', 'userIndex']);

//try to pass index from v-for up to body component
//to get whole objet, not just the name
const trigger = () => {
  getIndex(event)
   emit('selected', selectedUser, userIndex)
   
}

function getIndex(event) {  
  userIndex = event.target.selectedIndex - 1;
  return userIndex 
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
      @change="trigger($event)">
        <option disabled value="">Choose User</option>
        <option
        v-for="(userName, index) in usersLi"
        
        >{{ userName.name }}</option>
      </select>
    </div>
    </form>
    </div>
</template>

<style scoped>

</style>