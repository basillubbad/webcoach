<template>
  <header>
    <nav>
      <h1>
        <router-link to="/">WebCoach</router-link>
      </h1>
      <ul>
        <li>
          <router-link to="/coaches">All Coaches</router-link>
        </li>
        <li v-if="isLoggedIn">
          <router-link to="/requests">Requests</router-link>
        </li>
        <li v-else>
          <router-link to="/auth">Login</router-link>
        </li>
        <li v-if="isLoggedIn">
          <button class="btu" @click="lodout">Logout</button>
        </li>
      </ul>
    </nav>
  </header>
</template>
  
<script>

export default {
 
 computed: {
  isLoggedIn(){
    return this.$store.getters.isAuthenticated;
  }
    
  },
  methods:{
lodout(){
  this.$store.dispatch('logout')
  this.$router.replace('/coaches')
}
  }
}
</script>

<style scoped>
header {
  width: 100%;
  height: 5rem;
  background: rgb(23,20,85);
background: linear-gradient(227deg, rgba(23,20,85,1) 0%, rgba(157,2,254,1) 100%);
  display: flex;
  justify-content: center;
  align-items: center;
}

header a {
  text-decoration: none;
  color: #ede7ec;
  display: inline-block;
  padding: 0.75rem 1.5rem;
  border: 1px solid transparent;
}

a:active,
a:hover,
a.router-link-active {
  border: 1px solid #fcfcfc;
}

h1 {
  margin: 0;
}

h1 a {
  color: white;
  margin: 0;
}

h1 a:hover,
h1 a:active,
h1 a.router-link-active {
  border-color: transparent;
}

header nav {
  width: 90%;
  margin: auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

header ul {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

li {
  margin: 0 0.5rem;
}
.btu {
  text-decoration: none;
  padding: 0.75rem 1.5rem;
  font: inherit;
  background-color: #7706c300;
  border: 1px solid #3a0061;
  color: white;
  
  cursor: pointer;
  border-radius: 30px;
  margin-right: 0.5rem;
  display: inline-block;
}

.btu:hover,
.btu:active {
  background-color: rgba(117, 5, 187, 0.862);
  border-color: rgba(157,2,254,1);
}
</style>