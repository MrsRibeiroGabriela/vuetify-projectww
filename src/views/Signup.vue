<template>
  <div class="container">
    <!--    Logo Div-->
    <div class="row">
      <div class="col-12 text-center pt-3">
        <router-link :to="{ name: 'Home' }">
          <img id="logo" src="../assets/icon.png" />
        </router-link>
      </div>
    </div>

    <div class="row">
      <div class="col-12 justify-content-center d-flex flex-row pt-5">
        <div id="signup-div" class="flex-item border">
          <h2 class="pt-4 pl-4">Criar uma Conta</h2>
          <form @submit="signup" class="pt-4 pl-4 pr-4">
            <div class="form-group">
              <label>E-mail</label>
              <input
                type="email"
                class="form-control"
                v-model="email"
                required
              />
            </div>
            <div class="form-row">
              <div class="col">
                <div class="form-group">
                  <label>Primeiro Nome</label>
                  <input
                    type="name"
                    class="form-control"
                    v-model="firstName"
                    required
                  />
                </div>
              </div>
              <div class="col">
                <div class="form-group">
                  <label>Sobrenome</label>
                  <input
                    type="name"
                    class="form-control"
                    v-model="lastName"
                    required
                  />
                </div>
              </div>
            </div>
            <div class="form-group">
              <label>Senha</label>
              <input
                type="password"
                class="form-control"
                v-model="password"
                required
              />
            </div>
            <div class="form-group">
              <label>Confirme a senha</label>
              <input
                type="password"
                class="form-control"
                v-model="passwordConfirm"
                required
              />
            </div>
            <button type="submit" class="btn btn-primary mt-2 py-0">
              Criar Conta
            </button>
          </form>
          <hr />
          <small class="form-text text-muted pt-2 pl-4 text-center"
            >Você já possui uma conta?</small
          >
          <p class="text-center">
            <router-link
              class="btn btn-dark text-center mx-auto px-5 py-1 mb-2"
              :to="{ name: 'Signin' }"
              >Acesse Aqui</router-link
            >
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
var axios = require("axios");
import swal from "sweetalert";
export default {
  name: "Signup",
  props: ["baseURL"],
  data() {
    return {
      email: null,
      firstName: null,
      lastName: null,
      password: null,
      passwordConfirm: null,
    };
  },
  methods: {
    async signup(e) {
      e.preventDefault();
      // se as senhas forem iguais
      if (this.password === this.passwordConfirm) {
        
        const user = {
          email: this.email,
          firstName: this.firstName,
          lastName: this.lastName,
          password: this.password,
        };

        // chama a API
        await axios({
          method: "post",
          url: this.baseURL + "user/signup",
          data: JSON.stringify(user),
          headers: {
            "Content-Type": "application/json",
          },
        })
          .then(() => {
            // redireciona para a home page
            this.$router.replace("/");
            swal({
              text: "Usuário cadastrado com sucesso. Por favor, efetue o seu Login.",
              icon: "success",
              closeOnClickOutside: false,
            });
          })
          .catch((err) => {
            console.log(err);
          });
      } else {
        // senhas não são iguais
        swal({
          text: "Erro! As senhas informadas não são iguais.",
          icon: "error",
          closeOnClickOutside: false,
        });
      }
    },
  },
};
</script>

<style scoped>
.btn-dark {
  background-color: #e7e9ec;
  color: #000;
  font-size: smaller;
  border-radius: 0;
  border-color: #adb1b8 #a2a6ac #a2a6ac;
}

.btn-primary {
  background-color: #f0c14b;
  color: black;
  border-color: #a88734 #9c7e31 #846a29;
  border-radius: 0;
}

#logo {
  width: 150px;
}

@media only screen and (min-width: 992px) {
  #signup-div {
    width: 40%;
  }
}
</style>
