<template>
  <footer>
    <div class="container pt-5">
      <div class="row">

        <div class="col-md-3 col-6">
          <div class="align-top">
            <router-link class="navbar-brand" :to="{name : 'Home'}">
            <img id="logo" src="../assets/vila-yara-footer.png" />
            </router-link>
          </div>
        </div>

        <div class="col-md-3 col-6">
          <ul style="list-style-type: none">
            <li class="text-light font-weight-bold pb-2">Institucional</li>
            <li><a class="footer-link font-weight-light" href="#">Quem somos</a></li>
            <li><a class="footer-link font-weight-light" href="#">Trabalhe Conosco</a><br></li>
            <li><a class="footer-link font-weight-light" href="#">Políticas de Privacidade e Termos de Uso</a><br></li>
          </ul>
        </div>

        <div class="col-md-3 col-6">
          <ul style="list-style-type: none">
            <li class="text-light font-weight-bold">Redes Sociais</li>
            <li><a class="footer-link font-weight-light" href="#">Facebook</a></li>
            <li><a class="footer-link font-weight-light" href="#">Twitter</a><br></li>
            <li><a class="footer-link font-weight-light" href="#">Instagram</a><br></li>
          </ul>
        </div>

        <div class="col-md-3 col-6">
          <ul style="list-style-type: none">
            <li class="text-light font-weight-bold">Central de Atendimento</li>
            <li><a class="footer-link font-weight-light" href="#">(11) 4000-0000</a></li>
            <li><a class="footer-link font-weight-light" href="#">Fale Conosco</a><br></li>
            <li><a class="footer-link font-weight-light" href="#">Dúvidas Frequentes</a><br></li>
          </ul>
        </div>

        
      </div>

      <!--<div class="row">
        <div class="col-12">
          <div class="text-center py-5">
          </div>
        </div>
      </div>-->
    </div>
  </footer>
</template>

<script>
export default {
  name : "Footer"
}
</script>

<style>
footer {
  margin-top : 100px;
  background-color:#FAAA28;
  font-size:16px;
}

li {
  padding-left: 0;
  padding-bottom: 10px;
}

a {
  text-decoration: none;
}

.footer-link {
  color: #DDD;
}

#logo {
  width: 200px;
}

footer {
  font-family: 'Roboto', sans-serif;
}


</style>
