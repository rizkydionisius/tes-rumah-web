<script setup>
import { ref, computed } from 'vue';
import axios from 'axios';

const users = ref([]);
const selectedUser = ref(null);
const searchQuery = ref('');

const filteredUsers = computed(() => {
  if (!searchQuery.value) return users.value;
  return users.value.filter(user =>
    user.email.toLowerCase().includes(searchQuery.value.toLowerCase())
  );
});

const fetchUsers = async () => {
  try {
    const response = await axios.get('https://jsonplaceholder.typicode.com/users');
    users.value = response.data;
  } catch (error) {
    console.error('Error fetching users:', error);
  }
};

const fetchUserDetail = async (id) => {
  try {
    const response = await axios.get(`https://jsonplaceholder.typicode.com/users/${id}`);
    selectedUser.value = response.data;
  } catch (error) {
    console.error('Error fetching user detail:', error);
  }
};

// Search user by email
const searchUserByEmail = async () => {
  try {
    const response = await axios.get(`https://jsonplaceholder.typicode.com/users?email=${searchQuery.value}`);
    users.value = response.data;
  } catch (error) {
    console.error('Error searching user by email:', error);
  }
};

fetchUsers();
</script>

<template>
  <div>
    <h1>User Management App</h1>

    <!-- Search bar -->
    <input 
      v-model="searchQuery" 
      placeholder="Search by email..." 
      @input="searchUserByEmail" 
    />

    <!-- User list -->
    <ul>
      <li v-for="user in filteredUsers" :key="user.id">
        <a href="#" @click.prevent="fetchUserDetail(user.id)">{{ user.name }}</a>
        <p>Email: {{ user.email }}</p>
        <p>Address: {{ user.address.street }}, {{ user.address.city }}</p>
      </li>
    </ul>

    <!-- User details -->
    <div v-if="selectedUser">
      <h2>Details for {{ selectedUser.name }}</h2>
      <p><strong>Email:</strong> {{ selectedUser.email }}</p>
      <p><strong>Phone:</strong> {{ selectedUser.phone }}</p>
      <p><strong>Website:</strong> {{ selectedUser.website }}</p>
      <p><strong>Company:</strong> {{ selectedUser.company.name }}</p>
      <p><strong>Address:</strong> {{ selectedUser.address.street }}, {{ selectedUser.address.city }}</p>
    </div>
  </div>
</template>