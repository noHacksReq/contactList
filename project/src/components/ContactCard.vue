<script setup="ts">
import { ref } from 'vue';

const props = defineProps({
  selectedUser: {
    type: Object
  }
});

</script>

<template>
    <div>
      <h3>Contact Info</h3>
      <div>
        <h4>{{ selectedUser.name }}</h4>
        <p>{{ selectedUser.email }}</p>
      </div>  
      
    </div>
</template>

<style scoped>

</style>