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
      <h3 id="cardTitle">Contact Info</h3>
      <div id="infoCont">
        <h4>Name: {{ selectedUser.name }}</h4>
        <p>Username: {{ selectedUser.username }}</p>
        <p>Email: {{ selectedUser.email }}</p>
        <p>Phone: {{ selectedUser.phone }}</p>
        <p id="link">Website <a href="{{ selectedUser.website }}" _target="blank">{{ selectedUser.website }}</a></p>
      </div>  
      
    </div>
</template>

<style scoped>

#contactCardCont {
  background-color: #978e8e;
  display: flex;
  flex-direction: column;
  align-items: flex-start;

  border-radius: 25px;
  filter: drop-shadow(2px 4px 6px #7a88b3);
}

#infoCont {
  width: 100%;
  justify-items: flex-start;
}

#infoCont h4, p {
  width: inherit;
  text-align: left;
  padding-left: 10px;
}

#cardTitle {
  align-self: center;
}

#link a {
  font-size: 25px;
  color: #34346a;
}

</style>