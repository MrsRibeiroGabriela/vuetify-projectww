<template>
  <div class="container">
    <div class="row">
      <div class="col-12 text-center">
        <h4 class="pt-3">Editar Produto</h4>
      </div>
    </div>

    <div class="row">
      <div class="col-3"></div>
      <div class="col-md-6 px-5 px-md-0">
        <form v-if="product">
          <div class="form-group">
            <label>Categoria</label>
            <select class="form-control" v-model="product.categoryId" required>
              <option v-for="category of categories" :key="category.id" :value="category.id">{{category.categoryName}}</option>
            </select>
          </div>
          <div class="form-group">
            <label>Nome</label>
            <input type="text" class="form-control" v-model="product.name" required>
          </div>
          <div class="form-group">
            <label>Descrição</label>
            <textarea class="form-control" v-model="product.description" required></textarea>
          </div>
          <div class="form-group">
            <label>URL da Imagem</label>
            <input type="url" class="form-control" v-model="product.imageURL" required>
          </div>
          <div class="form-group">
            <label>Preço</label>
            <input type="number" class="form-control" v-model="product.price" required>
          </div>
          <button type="button" class="btn btn-primary" @click="editProduct">Submeter</button>
        </form>
      </div>
      <div class="col-3"></div>
    </div>
  </div>
</template>

<script>
var axios =  require('axios')
import swal from 'sweetalert';
export default {
  data(){
    return {
      product: null
    }
  },
  props : ["baseURL", "products", "categories"],
  methods : {
    async editProduct() {
      axios.post(this.baseURL+"product/update/"+this.id, this.product)
      .then(() => {
        
        this.$emit("fetchData");
        this.$router.push({name : 'AdminProduct'});
        swal({
          text: "Produto Atualizado com Sucesso!",
          icon: "success",
          closeOnClickOutside: false,
        });
      })
      .catch(err => console.log("err", err));
    }
  },
  mounted() {
    if (!localStorage.getItem('token')) {
      this.$router.push({name : 'Signin'});
      return;
    }
    this.id = this.$route.params.id;
    this.product = this.products.find(product => product.id == this.id);
  }
}
</script>

<style scoped>
h4 {
  font-family: 'Roboto', sans-serif;
  color: #484848;
  font-weight: 700;
}

</style>
