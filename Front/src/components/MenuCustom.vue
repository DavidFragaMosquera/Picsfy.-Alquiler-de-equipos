<template>

  <div id="nav">
      <h1>PICSFY</h1>
      <p><router-link :to="{ name:'Home'}"> Home</router-link></p>
      <p v-show="!seeIsLogged"><router-link :to="{ name:'Login'}" > Login </router-link></p>
      <p><router-link :to="{ name:'Products'}">Productos</router-link></p>
      <p  v-show="!seeIsLogged"><router-link :to="{ name:'NewUser'}"> Registrate </router-link></p>
      <p  v-show="seeIsLogged"><router-link :to="{ name:'Profile'}"> Mi perfil </router-link></p>
      <p><router-link :to="{ name:'About'}"> About</router-link></p>

      <br/>
      <button class="cerrar" @click="logoutUser()" v-show="seeIsLogged">Logout</button>
    </div>
</template>

<script>
import { clearlogin, clearAuthToken, clearId, isLogged } from "../aux/helpers.js";
export default {
  name: "MenuCustom",
  data() {
    return {
      seeIsLogged: false
    }
  },
  methods: {
    logoutUser() {
      clearlogin();
      clearAuthToken();
      clearId();
      this.$router.push("/user/logIn");
      location.reload();
    },
    showIsLogged(){
      this.seeIsLogged = isLogged();
    }
  },
  created() {
    this.showIsLogged();
  }
};

</script>

<style scoped>

#nav{ 
  display: flex;
  text-decoration: none;
  justify-content: flex-end;
  padding-right: 5rem;
  background: rgba(189, 177, 189, 0.089);
  font-weight: bold;
  box-shadow: 0px 8px 6px -6px rgba(78, 90, 100, 0.479); 

}
#nav p{
  padding: 0.75rem; 
  border-right: 1.5px solid rgba(255, 255, 255, 0.205);
  text-decoration: none;
  color: black;
}

#nav h1{
  align-items: flex-start;
  padding-right: 50rem;
  font-weight: bold;
  font-size: 2rem;
  letter-spacing: 30px;
}

#nav p:last-child{
  border-right: none;
}
button{
  padding: 1rem 2rem;
  border: none;
  border-radius: 12px;
  font-size: 1rem;
  font-weight: bold;
  color: red;
  background: rgba#000000;
;
}
.regist{
  border-right: none;
  color: rgb(48, 175, 97);
}
.cerrar{
  background: none;
  box-shadow: none;
  color: orange;
  margin-top: -0.5rem;
}
</style>