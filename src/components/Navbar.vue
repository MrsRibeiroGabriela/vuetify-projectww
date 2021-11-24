<template>
  <nav class="navbar navbar-expand-lg navbar-custom">
<!--Logo-->
    <router-link class="navbar-brand" :to="{name : 'Home'}">
      <img id="logo" src="../assets/icon.png" />
    </router-link>

<!--Burger Button-->
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent"
     aria-expanded="false" aria-label="Toggle navigation">Menu
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="navbarSupportedContent">

<!--Search Bar-->
      <form class="form-inline ml-auto mr-auto">
        <div class="input-group">
          <input size="100" type="text" class="form-control" placeholder="O que você procura?" aria-label="Username" aria-describedby="basic-addon1">
          <div class="input-group-prepend">
            <span class="input-group-text" id="search-button-navbar">
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-search" viewBox="0 0 16 16">
                <path d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z"/>
              </svg>
            </span>
          </div>
        </div>
      </form>

<!--DropDowns-->
      <ul class="navbar-nav ml-auto">
        <li class="nav-item dropdown">
          <a class="nav-link text-light dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
            Navegação
          </a>
          <div class="dropdown-menu" aria-labelledby="navbarDropdown">
            <router-link class="dropdown-item" :to="{name : 'Home'}" >Home</router-link>
            <router-link class="dropdown-item" :to="{name : 'Product'}">Produtos</router-link>
            <router-link class="dropdown-item" :to="{name : 'Category'}">Categorias</router-link>
          </div>
        </li>

        <li class="nav-item dropdown">
          <a class="nav-link text-light dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
            Acessos
          </a>
          <div class="dropdown-menu" aria-labelledby="navbarDropdown">
            <router-link class="dropdown-item" v-if="!token" :to="{name: 'Signin'}">Sign in</router-link>
            <router-link class="dropdown-item" v-else :to="{name : 'Wishlist'}" >Lista de Desejos</router-link>
            <router-link class="dropdown-item"  :to="{name: 'Admin'}">Admin</router-link>
            <router-link class="dropdown-item" v-if="!token" :to="{name: 'Signin'}">Log In</router-link>
            <router-link class="dropdown-item" v-if="!token" :to="{name: 'Signup'}">Sign Up</router-link>
            <a class="dropdown-item" v-if="token" href="#" @click="signout">Sign Out</a>
          </div>
        </li>

        <li class="nav-item">
          <router-link class="nav-link text-light" :to="{name : 'Order'}">Pedidos</router-link>
        </li>
        <li class="nav-item">
          <div id="cart">
            <span id="nav-cart-count">{{cartCount}}</span>
            <router-link class="text-light" :to="{name : 'Cart'}"><i class="fa fa-shopping-cart" style="font-size:36px"></i></router-link>
          </div>
        </li>
      </ul>
    </div>
  </nav>

</template>

<script>
import swal from 'sweetalert';
export default {
  name : "Navbar",
  props: ["cartCount"],
  data() {
    return {
      token: null
    }
  },
  methods: {
    signout() {
      localStorage.removeItem('token');
      this.token = null;
      this.$router.push({name:'Home'});
      swal({
        text: "Você não está logado. Por favor, acesse novamente.",
        icon: "success",
        closeOnClickOutside: false,
      });
    }
  },
  mounted() {
    this.token = localStorage.getItem('token');
  }
}
</script>

<style scoped>
  #logo {
    width: 150px;
    margin-left: 20px;
    margin-right: 20px;
  }
  .navbar-custom {
    background-color: #8F0EFA;
  }
  .nav-link {
    color: rgba(255,255,255);
  }

  #search-button-navbar {
    background-color: #FAAA28;
    border-color: #FAAA28;
    border-top-right-radius: 5px;
    border-bottom-right-radius: 5px;
  }
  #nav-cart-count {
    background-color: #FAAA28;
    color: white;
    border-radius: 50%;
    position: absolute;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 15px;
    height: 15px;
    font-size: 15px;
    margin-left: 10px;
  }
  #cart {
    position: relative;
  }
  /* Medium devices */
  @media screen and (max-width: 1000px) {  
  *{
    display: flex;
    flex-direction: column;
    align-content: center;
    width: 1ev;
    height: auto;
  }  
  .input-group{
    flex-direction: row;
  }
  .form-control{
    height: 100%;
  }
  .input-group-prepend{
    background-color: #FAAA28;
    border-top-right-radius: 5px;
    border-bottom-right-radius: 5px;
  }
  .navbar-toggler-icon{
    position: absolute;
  }
  .navbar-toggler{
    border: solid 1px white;
    margin-bottom: 10px;
  }
  }
</style>
