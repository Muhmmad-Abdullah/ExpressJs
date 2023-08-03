<template>
  <div>
    <h1>Fetch Data using Vue </h1>
    <ul>
      <li v-for="user in users" :key="user.id">
        {{ user.id }} - {{ user.name }} - {{ user.education }} - {{ user.email }} - {{ user.address }} - {{ user.number }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      users: [],
    };
  },
  mounted() {
    this.fetchUsers();
  },
  methods: {
    async fetchUsers() {
      try {
        const response = await axios.get("http://localhost:8080");
        this.users = response.data;
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>
