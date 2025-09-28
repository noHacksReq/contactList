<script setup="ts">
import { ref } from 'vue';

const props = defineProps({
  selectedUser: {
    type: Object
  }
});

</script>

<template>
    <div id="contactCardCont">
      <h3>Contact Info</h3>
      <div>
        <h4>Name: {{ selectedUser.name }}</h4>
        <p>Username: {{ selectedUser.username }}</p>
        <p>Email: {{ selectedUser.email }}</p>
        <p>Phone: {{ selectedUser.phone }}</p>
        <p>Website <a href="{{ selectedUser.website }}" _target="blank">{{ selectedUser.website }}</a></p>
      </div>  
      
    </div>
</template>

<style scoped>

#contactCardCont {
  background-color: #978e8e;
  
}

</style>