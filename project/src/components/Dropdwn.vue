<script setup lang="ts">
import { ref } from 'vue';

let selectedUser = ref(null);
let userIndex = ref()
const props = defineProps({
  usersLi: Array,
  
});


const emit = defineEmits(['selected', 'userIndex']);

const trigger = (event: Event) => {
  getIndex(event)
  emit('selected', userIndex)
}

function getIndex(event: Event | null) {  
  
  userIndex = event.target.selectedIndex;  
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
          <option v-for="(userName, index) in usersLi">
            {{ userName.name }}
          </option>
          </select>
         </div>
      </form>
    </div>
</template>

<style scoped>
.dropCont {
  margin-bottom: 20px;
}
</style>