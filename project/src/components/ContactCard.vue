<script setup lang="ts">

const props = defineProps({
  selectedUser: { 
    id: Number, 
    name: String,
    username: String, 
    email: String, 
    address: Object,
    phone: String,  
    website: String, 
    company: Object
  }
});

</script>

<template>
    <div class="contactCardCont">
      <h3 class="cardTitle">Contact Info</h3>
      <div class="infoCont">
        <h4>Name: {{ selectedUser.name }}</h4>
        <p>Username: {{ selectedUser.username }}</p>
        <p>Email: {{ selectedUser.email }}</p>
        <p>Phone: {{ selectedUser.phone }}</p>
        <p class="link">Website <a href="{{ selectedUser.website }}" 
          _target="blank">{{ selectedUser.website }}</a></p>
      </div>  
      
    </div>
</template>

<style scoped>

.contactCardCont {
  background-color: #978e8e;
  display: flex;
  flex-direction: column;
  align-items: flex-start;

  border-radius: 25px;
  filter: drop-shadow(2px 4px 6px #7a88b3);
}

.infoCont {
  width: 100%;
  justify-items: flex-start;
}

.infoCont h4, p {
  width: inherit;
  text-align: left;
  padding-left: 10px;
}

.cardTitle {
  align-self: center;
}

.link a {
  font-size: 25px;
  color: #34346a;
}

</style>