<template>
    <header>
      <h1>Welcome to the Homepage</h1>
      <nav>
        <a href="/">Home</a>
        <a href="/apply">Apply</a>
        <a href="/userprofile">Profile</a>
        <!-- Attach the logout function with @click -->
        <button @click="logout">Logout</button>
      </nav>
    </header>
    <main>
      <p>This is the homepage. Feel free to explore!</p>
    </main>
  </template>
  
  <script>
  import axios from 'axios';

export default {
  methods: {
    async logout() {
      try {
        const response = await axios.get('http://localhost:5555/logout', { withCredentials: true });
        if (response.status === 200) {
          this.$router.push('/'); // Redirect to the login page after logout
        }
      } catch (error) {
        console.error('Error logging out:', error);
      }
    }
  }
};
  </script>
  
  <style scoped>
  header {
    background-color: #f8f9fa;
    padding: 20px;
    text-align: center;
    border-bottom: 1px solid #ddd;
  }
  
  nav a {
    margin: 0 10px;
    text-decoration: none;
    color: #007bff;
    font-weight: bold;
  }
  
  nav a:hover {
    text-decoration: underline;
  }
  
  main {
    padding: 20px;
  }
  </style>
  