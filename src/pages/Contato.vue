<template>
  <q-page padding>
    <div>
      <h4 class="text-center text-weight-bolder color-primary q-ma-lg text-azul_escuro">Contato</h4>
      <h5 class="text-center text-weight-bold q-ma-none q-mb-lg text-azul_escuro">CAPACITA - Cursos Inclusivos</h5>
      <p class="text-center" style="font-size: 1.5em;">Entre em contato conosco e tire suas dúvidas.</p>
    </div>
     <!-- FOOTER -->
    <div class="footer">
      <div class="q-pa-md q-px-xl row justify-center">
        <!-- LOGO -->
      <div class="logorodape" >
        <div class="col-xs-12 col-sm-2 flex justify-center ">
          <div class="q-pb-xl" style="width: 300px;">
            <q-img src="../imagens/logo_capacita_branca.png"/>
          </div>
        </div>
      </div>
        <!-- Coluna 1 -->
        <div class="col-xs-12 col-sm-2 flex justify-center">
          <div style="width: 100px;">
            <p><span>CAPACITA</span><br><br>
            <a href="#">Sobre Nós</a><br>
            <a href="#">Notícias</a><br>
            <a href="#">Contato</a></p>
          </div>
        </div>
        <!-- Coluna 2 -->
        <div class="col-xs-12 col-sm-2 flex justify-center">
          <div style="width: 100px;">
             <p><span>ENSINO</span><br><br>
              <a href="#">Cursos</a><br>
              <a href="#">Instituições</a><br>
              <a href="#">Fórum</a><br></p>
          </div>
        </div>
        <!-- Coluna 3 -->
        <div class="col-xs-12 col-sm-2 flex justify-center">
          <div  style="width: 100px;">
            <p>
              <span>ACESSO</span> <br><br>
              <a href="#">Cadastro</a> <br>
              <a href="#">Login</a>
            </p>
          </div>
        </div>
        <!-- BOTÕES -->
        <div class="col-xs-12 col-sm-2 flex justify-center">
          <div style="width: 120px;" class="q-gutter-y-sm">
            <q-btn color="orange" label="Registrar" style="width: 100px;"/>
            <q-btn color="white" text-color="orange" label="Entrar"  style="width: 100px"/>
          </div>
        </div>
      </div>
      <!-- COPY RIGHT -->
      <hr style="width: 90%; opacity: 30%">
      <p class="text-center q-mb-none q-pa-sm">© Copyright 2020</p>
    </div>
  </q-page>
</template>

<style lang="stylus">
//TEXTO
.imagemsobrenos{
  padding: 0px 60px 0px 0px
}
//FOOTER
div.footer {
  padding-top: 2%;
  width: 100%;
  background-color: $primary;
}
.footer p span {
  color: orange;
  font-weight:600;
}
.footer{
font-size: 20px;
}
.footer a {
  text-decoration: none;
  color: #ffffff;
}
.footer a:hover {
  color: $azul_escuro;
  font-weight: 800;
}
</style>
