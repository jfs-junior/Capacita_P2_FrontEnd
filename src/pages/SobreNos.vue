<template>
  <q-page>
    <div align="center">
      <div class="imagemsobrenos">
        <q-img src="../imagens/logo_capacita.png" class="img_principal"/>
        <h4 class="text-center text-weight-bolder color-primary q-ma-lg text-azul_escuro">SOBRE NÓS</h4>
        <div class="textosobrenos">
        <p class="text-justify" style="font-size: 1.5em;">Nossa missão é trazer para você os melhores cursos profissionalizantes. Através de uma rede de instituições de ensino, sua Capacitação estará garantida para o mercado de trabalho.

        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec bibendum efficitur augue quis laoreet. Quisque facilisis tellus non tempus consectetur. Integer aliquet lorem at augue malesuada feugiat. Fusce accumsan, velit sed semper condimentum, sem felis fringilla dolor, hendrerit posuere tellus odio eu diam. Donec molestie iaculis commodo. Maecenas elit diam, ullamcorper ut ligula vitae, commodo dictum metus. Suspendisse vitae maximus felis, finibus ullamcorper velit. Morbi blandit ex non ullamcorper bibendum. In tempus ligula in nunc cursus pellentesque vel nec leo. Mauris eu leo blandit, tempus magna eu, consequat ante. Fusce fringilla nibh in velit dictum, non maximus risus maximus. Integer a mattis purus. Quisque ipsum leo, finibus non turpis quis, aliquam tincidunt ex. Donec scelerisque varius elit, nec lacinia tellus volutpat nec. Etiam quis turpis malesuada velit lacinia luctus a sed ante. Suspendisse semper posuere risus, et scelerisque neque commodo sed.
        Suspendisse in ante nec enim malesuada auctor ut in purus. Etiam in purus sed nibh tincidunt consectetur. Nam aliquet ac libero non vehicula. Vivamus porta, libero a dignissim gravida, mauris velit imperdiet libero, vitae accumsan orci arcu eget enim. Vestibulum est neque, volutpat sed lorem ut, pellentesque maximus tortor. Suspendisse vel leo sollicitudin, sagittis ex et, ultrices felis. Vestibulum semper erat in scelerisque malesuada. Morbi accumsan diam risus, quis eleifend mi interdum faucibus. Phasellus bibendum nisi ut eleifend cursus. Vivamus quis volutpat libero. Integer euismod et turpis vel suscipit. Nullam imperdiet imperdiet ex sed tempus. In porta pellentesque eros, eu blandit nibh pellentesque a.
        </p>
        </div>
      </div>

      <!-- BOTOES -->
      <div class="row justify-center col-12 col-12 q-pa-sm q-pb-lg text-azul_escuro" style="min-width: 250px; max-width: 400px;">
        <div class="col-3" align="center">
          <a href="#" class="link-primario text-azul_escuro">
            <img src="../imagens/btn_acesso.svg" alt="Botão de Inicial" class="text-center" style="width: 3em; width: 4em;"><br>
            <span>Início</span>
          </a>
        </div>
        <div class="col-3" align="center">
          <a href="/cursos" class="link-primario text-azul_escuro">
            <img src="../imagens/btn_cursos.svg" alt="Botão de Inicial" style="width: 3em;  width: 4em;"><br>
            <span>Cursos</span>
          </a>
        </div>
        <div class="col-3" align="center">
          <a href="#" class="link-primario text-azul_escuro">
            <img src="../imagens/btn_forum.svg" alt="Botão de Inicial" style="width: 3em;  width: 4em;"><br>
            <span>Fórum</span>
          </a>
        </div>
        <div class="col-3" align="center">
          <a href="#" class="link-primario text-azul_escuro">
            <img src="../imagens/btn_noticias.svg" alt="Botão de Inicial" style="width: 3em;  width: 4em;"><br>
            <span>Notícias</span>
          </a>
        </div>
      </div>
      <!-- CARDS CIRCULARES -->
      <div style="min-width: 300px; max-width: 800px;">
        <div class="row justify-center col-12 col-12 q-pa-sm">
          <div  class="col-6 col-sm-4 col-md-2 q-pa-sm relative-position flex items-center justify-center"
                align="center"
                @mouseover="fisico = true"
                @mouseleave="fisico = false"
          >
            <div class="absolute flex items-center justify-center card-selecao" v-show="fisico"><span>FÍSICO</span></div>
            <div class="card-circulares card-fisico"></div>
          </div>
          <div  class="col-6 col-sm-4 col-md-2 q-pa-sm relative-position flex items-center justify-center"
                align="center"
                @mouseover="visual = true"
                @mouseleave="visual = false"
          >
            <div class="absolute flex items-center justify-center card-selecao" v-show="visual"><span>VISUAL</span></div>
            <div class="card-circulares card-visual"></div>
          </div>
          <div  class="col-6 col-sm-4 col-md-2 q-pa-sm relative-position flex items-center justify-center"
                align="center"
                @mouseover="mudez = true"
                @mouseleave="mudez = false"
          >
            <div class="absolute flex items-center justify-center card-selecao" v-show="mudez"><span>MUDEZ</span></div>
            <div class="card-circulares card-mudez"></div>
          </div>
          <div  class="col-6 col-sm-4 col-md-2 q-pa-sm relative-position flex items-center justify-center"
                align="center"
                @mouseover="auditivo = true"
                @mouseleave="auditivo = false"
          >
            <div class="absolute flex items-center justify-center card-selecao" v-show="auditivo"><span>AUDITIVO</span></div>
            <div class="card-circulares card-auditivo"></div>
          </div>
          <div  class="col-6 col-sm-4 col-md-2 q-pa-sm relative-position flex items-center justify-center"
                align="center"
                @mouseover="mental = true"
                @mouseleave="mental = false"
          >
            <div class="absolute flex items-center justify-center card-selecao" v-show="mental"><span>MENTAL</span></div>
            <div class="card-circulares card-mental"></div>
          </div>
          <div  class="col-6 col-sm-4 col-md-2 q-pa-sm relative-position flex items-center justify-center"
                align="center"
                @mouseover="multiplos = true"
                @mouseleave="multiplos = false"
          >
            <div class="absolute flex items-center justify-center card-selecao" v-show="multiplos"><span>MÚLTIPLOS</span></div>
            <div class="card-circulares card-multiplos"></div>
          </div>
        </div>
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
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'PageSobreNos',
  data () {
    return {
      fisico: false,
      visual: false,
      mudez: false,
      auditivo: false,
      mental: false,
      multiplos: false
    }
  }
}
</script>

<style lang="stylus">
.img_principal {
  max-width: 400px;
}
//IMAGEM E TEXTO SOBRE NOS
.imagemsobrenos{
  padding: 20px 20px 0px 20px
}
.textosobrenos{
  max-width: 1000px;
  text-align: justify;
}
//CSS CARTOES DOS TIPOS DE DEFICIENCIA
.card-circulares {
  background-size: 90%;
  background-position: top;
  border-radius: 100%;
  width: 120px;
  height: 120px;
}
.card-selecao {
  border-radius: 100%;
  background-color: rgba(#0D3759, 0.8);
  background-blend-mode: multiply;
  color: #ffffff;
  width: 120px;
  height: 120px;
  vertical-align: middle;
  font-weight: 500;
}
.card-fisico {
  background-image: url("../imagens/cartao_fisico.png");
}
.card-visual {
  background-image: url("../imagens/cartao_visual.png");
}
.card-mudez {
  background-image: url("../imagens/cartao_mudez.png");
}
.card-auditivo {
  background-image: url("../imagens/cartao_auditivo.png");
}
.card-mental {
  background-image: url("../imagens/cartao_mental.png");
}
.card-multiplos {
  background-image: url("../imagens/cartao_multiplos.png");
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
