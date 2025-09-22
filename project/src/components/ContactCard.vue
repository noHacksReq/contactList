<script setup="ts">
import { ref } from 'vue';

const props = defineProps({
  usersLi: Array,
  userName: String,
  selectedUser: Object
});

</script>

<template>
    <div>
      <h3>Contact Info</h3>
      <h4>{{ userName }}</h4>
      <div>email</div>
      <p >Phone number</p>
      <p>address</p>
    </div>
</template>

<style scoped>

</style>