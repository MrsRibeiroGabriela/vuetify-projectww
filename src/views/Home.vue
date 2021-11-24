<template>
  <div id="home">
    <!-- Page Wrapper
    <div id="background-div" class="page-holder bg-cover">

      <div class="container py-5">
        <header class="text-center text-white py-5">
          <h3 class="mb-4 rounded"><a href="#start-shopping" class="bg-white px-2 py-2 rounded" id="heading">Seja Bem-vindo(a) ao Supermercado Vila Yara</a></h3>
          <p id="content" class="lead mb-0 bg-dark p-1 rounded">A qualidade dos produtos e atendimento que você já conhece nas lojas físicas, agora, no mundo virtual.</p>
        </header>
      </div>
    </div>-->
    <!--Carousel-->
    <!--<div id="carouselExampleControls" class="carousel slide" data-ride="carousel">
    <ol class="carousel-indicators">
      <li data-target="#carouselExampleIndicators" data-slide-to="0" class="active"></li>
      <li data-target="#carouselExampleIndicators" data-slide-to="1"></li>
      <li data-target="#carouselExampleIndicators" data-slide-to="2"></li>
    </ol>
    <div class="carousel-inner">
      <div class="carousel-item active">
        <img class="d-block w-100" src="../assets/banner-modelo1.png" alt="banner-familia" style="width: 100%; height: auto;">
      </div>
      <div class="carousel-item">
        <img class="d-block w-100" src="../assets/banner-modelo2.png" alt="hortifruti" style="width:100%; height: auto;">
      </div>
      <div class="carousel-item">
        <img class="d-block w-100" src="../assets/banner-modelo3.png" alt="carrinho-de-supermercado" style="width:100%; height: auto;">
      </div>

    </div>
    <a class="carousel-control-prev" href="#carouselExampleIndicators" role="button" data-slide="prev">
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="sr-only">Previous</span>
    </a>
    <a class="carousel-control-next" href="#carouselExampleIndicators" role="button" data-slide="next">
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="sr-only">Next</span>
    </a>
</div>-->
  <div id="carouselExampleFade" class="carousel slide carousel-fade" data-ride="carousel">
  <div class="carousel-inner">
    <div class="carousel-item active">
      <img class="d-block w-100" src="../assets/banner1.png" alt="First slide">
    </div>
    <div class="carousel-item">
      <img class="d-block w-100" src="../assets/banner2.png" alt="Second slide">
    </div>
    <div class="carousel-item">
      <img class="d-block w-100" src="../assets/banner3.png" alt="Third slide">
    </div>
  </div>
  <a class="carousel-control-prev" href="#carouselExampleFade" role="button" data-slide="prev">
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
    <span class="sr-only">Previous</span>
  </a>
  <a class="carousel-control-next" href="#carouselExampleFade" role="button" data-slide="next">
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
    <span class="sr-only">Next</span>
  </a>
</div>

    <div id="start-shopping" class="container">
      <div class="row">
        <div class="col-12 text-left">
          <h2 class="pt-3">Categorias Mais Acessadas</h2>
        </div>
      </div>
      <div class="row">
        <div v-for="index in this.category_size" :key="index" class="col-md-6 col-xl-4 col-12 pt-3  justify-content-around d-flex">
          <CategoryBox :category="categories[index-1]">
          </CategoryBox>
        </div>
      </div>
    </div>

    <hr>
    <div class="container">
      <div class="row">
        <div class="col-12 text-left">
          <h2 class="pt-3">Produtos Mais Acessados</h2>
        </div>
      </div>
      <div class="row">
        <div v-for="index in this.product_size" :key="index" class="col-md-6 col-xl-4 col-12 pt-3  justify-content-around d-flex">
          <ProductBox :product="products[index-1]">
          </ProductBox>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import ProductBox from "../components/Product/ProductBox";
  import CategoryBox from "../components/Category/CategoryBox";

  export default {
    name: 'Home',
    components : { ProductBox, CategoryBox},
    props : ["baseURL", "products", "categories"],
    data(){
      return{
        category_size:0,
        product_size:0
      }
    },
    mounted(){
      this.category_size = this.categories.length;
      this.category_size = Math.min(6, this.category_size);

      this.product_size = this.products.length;
      this.product_size = Math.min(8, this.product_size);
    }
  }
</script>

<style>
  /*.page-holder {
    min-height: 50vh;
    box-shadow: inset 0 2500px 0 0 rgb(0 0 0 / 55%);
  }
  .bg-cover {
    background-size: cover !important;
  }
  #background-div {
    background: url(../assets/home.jpg)  center no-repeat;
  }
  */
  .carousel slide{
    min-height: 100vh;
    height: auto;
    width: auto;
    overflow: hidden;
  }
  #heading {
    text-decoration: none;
    font-family: 'Roboto', sans-serif;
    font-weight: 400;
    opacity: 0.8;
    font-family: 'Josefin Sans', sans-serif;
    color: #FAAA28;
  }

  #content {
    opacity: 0.8;
  }

  h2 {
    font-family: 'Josefin Sans', sans-serif;
  }
</style>
