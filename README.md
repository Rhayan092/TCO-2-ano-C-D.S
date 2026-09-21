# TCO-2-ano-C-D.S
VivaSaúde é um sistema web de informações sobre saúde, com conteúdos sobre sintomas, alimentação, saúde mental, primeiros socorros e orientações para situações de emergência.
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>VivaSaúde</title>

<style>

*{
  box-sizing:border-box;
  margin:0;
  padding:0;
}

body{
  font-family:Arial, sans-serif;
  min-height:100vh;
  color:white;

  background:
    radial-gradient(circle at 90% 5%,rgba(44,230,192,.25),transparent 28%),
    radial-gradient(circle at 0% 60%,rgba(52,150,255,.20),transparent 30%),
    linear-gradient(145deg,#061b26,#073c42 55%,#075b59);

  padding-bottom:100px;
}

button{
  font-family:inherit;
  cursor:pointer;
}

.topo{
  padding:22px 18px 10px;
  display:flex;
  justify-content:space-between;
  align-items:center;
}

.logo{
  display:flex;
  align-items:center;
  gap:10px;
}

.logo-icon{
  width:46px;
  height:46px;
  border-radius:15px;

  display:flex;
  align-items:center;
  justify-content:center;

  font-size:25px;

  background:linear-gradient(135deg,#35e0bd,#1597ff);
}

.logo h1{
  font-size:21px;
}

.logo span{
  color:#46e4c3;
}

.perfil-btn{
  width:44px;
  height:44px;
  border-radius:50%;
  border:1px solid rgba(255,255,255,.15);
  color:white;
  background:rgba(255,255,255,.09);
  font-size:20px;
}

.pagina{
  display:none;
}

.pagina.ativa{
  display:block;
}

.hero{
  position:relative;
  overflow:hidden;

  margin:22px 18px;
  padding:26px 22px;

  min-height:210px;

  border-radius:28px;

  background:linear-gradient(135deg,#1ed3af,#0e777e);

  box-shadow:0 20px 50px rgba(0,0,0,.25);
}

.hero h2{
  max-width:280px;
  margin:10px 0;

  font-size:27px;
  line-height:1.15;
}

.hero p{
  max-width:280px;

  font-size:13px;
  line-height:1.5;

  color:rgba(255,255,255,.8);
}

.hero small{
  font-size:11px;
  opacity:.8;
}

.medico{
  position:absolute;
  right:12px;
  bottom:8px;
  font-size:78px;
}

.pesquisa{
  display:flex;
  gap:8px;
  margin:20px 18px;
}

.pesquisa input{
  flex:1;
  min-width:0;

  padding:17px 18px;

  border-radius:18px;
  border:1px solid rgba(255,255,255,.14);

  outline:none;

  background:rgba(255,255,255,.09);
  color:white;

  font-size:14px;
}

.pesquisa input::placeholder{
  color:rgba(255,255,255,.55);
}

.pesquisa button{
  width:56px;

  border:0;
  border-radius:18px;

  color:white;
  font-size:20px;

  background:linear-gradient(135deg,#35e0bd,#1597ff);
}

.titulo{
  margin:28px 20px 15px;

  display:flex;
  justify-content:space-between;
  align-items:center;
}

.titulo h3{
  font-size:18px;
}

.titulo span{
  font-size:11px;
  color:#54dfc3;
}

.categorias{
  display:grid;
  grid-template-columns:repeat(2,1fr);
  gap:13px;

  padding:0 18px;
}

.card{
  min-height:145px;
  padding:18px;

  text-align:left;
  color:white;

  border-radius:23px;
  border:1px solid rgba(255,255,255,.10);

  background:rgba(255,255,255,.08);

  backdrop-filter:blur(15px);
}

.card:active{
  transform:scale(.96);
}

.icone{
  width:47px;
  height:47px;

  margin-bottom:14px;

  border-radius:15px;

  display:flex;
  align-items:center;
  justify-content:center;

  background:rgba(255,255,255,.12);

  font-size:24px;
}

.card h4{
  margin-bottom:6px;
  font-size:14px;
}

.card p{
  font-size:11px;
  line-height:1.4;
  color:rgba(255,255,255,.55);
}

.emergencia{
  width:calc(100% - 36px);

  margin:0 18px;
  padding:21px;

  display:flex;
  align-items:center;
  gap:15px;

  text-align:left;

  border:0;
  border-radius:24px;

  color:white;

  background:linear-gradient(135deg,#ff5265,#bd2949);
}

.emergencia-icon{
  font-size:38px;
}

.emergencia h3{
  font-size:16px;
  margin-bottom:5px;
}

.emergencia p{
  font-size:11px;
  color:rgba(255,255,255,.78);
}

.emergencia strong{
  display:block;
  margin-top:5px;
  font-size:20px;
}

.dica{
  margin:25px 18px;
  padding:21px;

  border-radius:23px;

  background:rgba(255,255,255,.07);
}

.dica-title{
  display:flex;
  gap:9px;
  align-items:center;
  margin-bottom:10px;
}

.dica p{
  font-size:12px;
  line-height:1.6;
  color:rgba(255,255,255,.65);
}

.menu{
  position:fixed;

  left:15px;
  right:15px;
  bottom:14px;

  height:68px;

  z-index:100;

  display:flex;
  align-items:center;
  justify-content:space-around;

  border-radius:23px;

  border:1px solid rgba(255,255,255,.10);

  background:rgba(4,25,32,.94);

  backdrop-filter:blur(18px);

  box-shadow:0 15px 40px rgba(0,0,0,.35);
}

.menu-item{
  border:0;
  background:transparent;

  color:rgba(255,255,255,.48);

  font-size:10px;
}

.menu-item div{
  margin-bottom:4px;
  font-size:21px;
}

.menu-item.ativo{
  color:#4ce5c6;
}

.voltar{
  margin:18px;

  border:0;
  background:transparent;

  color:#55dfc3;

  font-size:15px;
}

.pagina > h2{
  margin:0 20px 8px;
  font-size:25px;
}

.subtitulo{
  margin:0 20px;
  color:rgba(255,255,255,.60);
  font-size:13px;
}

.resultado{
  margin:14px 18px;
  padding:19px;

  border-radius:21px;

  border:1px solid rgba(255,255,255,.09);

  background:rgba(255,255,255,.08);
}

.resultado h3{
  margin-bottom:8px;
  font-size:16px;
}

.resultado p{
  color:rgba(255,255,255,.67);
  font-size:12px;
  line-height:1.6;
}

.resultado strong{
  color:#54dfc3;
}

.favorito-btn{
  float:right;

  border:0;
  background:transparent;

  color:white;

  font-size:22px;
}

.perfil-box,
.form-perfil{
  margin:20px 18px;
  padding:22px;

  border-radius:23px;

  background:rgba(255,255,255,.08);

  border:1px solid rgba(255,255,255,.08);
}

.form-perfil input{
  width:100%;

  margin-bottom:12px;
  padding:15px;

  border-radius:15px;

  border:1px solid rgba(255,255,255,.12);

  outline:none;

  color:white;

  background:rgba(255,255,255,.08);
}

.form-perfil input::placeholder{
  color:rgba(255,255,255,.5);
}

.botao-principal{
  width:100%;

  padding:15px;

  border:0;
  border-radius:15px;

  color:white;

  font-weight:bold;

  background:linear-gradient(135deg,#35e0bd,#1597ff);
}

.emergencia-grande{
  margin:20px 18px;
  padding:30px 22px;

  text-align:center;

  border-radius:27px;

  background:linear-gradient(135deg,#ff5265,#bd2949);
}

.emergencia-emoji{
  font-size:55px;
  margin-bottom:10px;
}

.emergencia-grande h2{
  margin-bottom:15px;
}

.emergencia-grande p{
  color:rgba(255,255,255,.8);
  line-height:1.5;
  margin-bottom:15px;
}

.emergencia-grande strong{
  display:block;
  font-size:30px;
  margin-bottom:20px;
}

.mensagem{
  margin:20px 18px;
  padding:18px;

  border-radius:18px;

  background:rgba(53,224,189,.12);

  color:#7cebd3;

  text-align:center;
}

</style>
</head>

<body>

<header class="topo">

  <div class="logo">

    <div class="logo-icon">🩺</div>

    <h1>
      Viva<span>Saúde</span>
    </h1>

  </div>

  <button
    class="perfil-btn"
    onclick="abrir('perfil')">
    👤
  </button>

</header>


<main>

<!-- INÍCIO -->

<section id="inicio" class="pagina ativa">

  <div class="hero">

    <small>SEJA BEM-VINDO 👋</small>

    <h2 id="saudacao">
      Cuide da sua saúde com informação.
    </h2>

    <p>
      Encontre informações rápidas, simples e organizadas
      para cuidar melhor de você.
    </p>

    <div class="medico">
      👩‍⚕️
    </div>

  </div>


  <div class="pesquisa">

    <input
      id="busca"
      placeholder="O que você está procurando?">

    <button onclick="pesquisar()">
      🔎
    </button>

  </div>


  <div id="resultadoHome"></div>


  <div class="titulo">

    <h3>Explore por categoria</h3>

    <span>VivaSaúde</span>

  </div>


  <div class="categorias">

    <button
      class="card"
      onclick="categoria('Primeiros socorros')">

      <div class="icone">🩹</div>

      <h4>Primeiros socorros</h4>

      <p>
        Cuidados em situações de emergência.
      </p>

    </button>


    <button
      class="card"
      onclick="categoria('Saúde mental')">

      <div class="icone">🧠</div>

      <h4>Saúde mental</h4>

      <p>
        Bem-estar emocional e psicológico.
      </p>

    </button>


    <button
      class="card"
      onclick="categoria('Nutrição')">

      <div class="icone">🥗</div>

      <h4>Nutrição</h4>

      <p>
        Alimentação e hábitos saudáveis.
      </p>

    </button>


    <button
      class="card"
      onclick="categoria('Sintomas')">

      <div class="icone">❤️</div>

      <h4>Sintomas</h4>

      <p>
        Informações sobre sintomas comuns.
      </p>

    </button>

  </div>


  <div class="titulo">

    <h3>Precisa de ajuda?</h3>

  </div>


  <button
    class="emergencia"
    onclick="abrir('emergencia')">

    <div class="emergencia-icon">
      🚨
    </div>

    <div>

      <h3>Emergência médica</h3>

      <p>
        Em uma emergência, procure atendimento imediatamente.
      </p>

      <strong>SAMU 192</strong>

    </div>

  </button>


  <div class="dica">

    <div class="dica-title">

      <span>💡</span>

      <h3>Você sabia?</h3>

    </div>

    <p>
      O VivaSaúde reúne informações para facilitar
      o acesso a conteúdos de saúde.
    </p>

  </div>

</section>


<!-- PESQUISA -->

<section id="pesquisa" class="pagina">

  <button
    class="voltar"
    onclick="abrir('inicio')">
    ← Voltar
  </button>

  <h2>🔎 Pesquisar</h2>

  <p class="subtitulo">
    Procure informações no VivaSaúde.
  </p>


  <div class="pesquisa">

    <input
      id="busca2"
      placeholder="Ex: febre, gripe, ansiedade...">

    <button onclick="pesquisar2()">
      🔎
    </button>

  </div>


  <div id="resultadoPesquisa"></div>

</section>


<!-- PERFIL -->

<section id="perfil" class="pagina">

  <button
    class="voltar"
    onclick="abrir('inicio')">
    ← Voltar
  </button>

  <h2>👤 Meu perfil</h2>


  <div id="perfilAtual"
       class="perfil-box">
  </div>


  <div class="form-perfil">

    <input
      id="nome"
      placeholder="Seu nome">

    <input
      id="email"
      placeholder="Seu e-mail"
      type="email">

    <input
      id="senha"
      placeholder="Crie uma senha"
      type="password">

    <button
      class="botao-principal"
      onclick="criarPerfil()">

      Criar meu perfil

    </button>

  </div>

</section>


<!-- FAVORITOS -->

<section id="favoritos" class="pagina">

  <button
    class="voltar"
    onclick="abrir('inicio')">
    ← Voltar
  </button>

  <h2>❤️ Favoritos</h2>

  <div id="listaFavoritos"></div>

</section>


<!-- CATEGORIA -->

<section id="categoriaPagina" class="pagina">

  <button
    class="voltar"
    onclick="abrir('inicio')">
    ← Voltar
  </button>

  <div id="categoriaConteudo"></div>

</section>


<!-- EMERGÊNCIA -->

<section id="emergencia" class="pagina">

  <button
    class="voltar"
    onclick="abrir('inicio')">
    ← Voltar
  </button>


  <div class="emergencia-grande">

    <div class="emergencia-emoji">
      🚨
    </div>

    <h2>Emergência</h2>

    <p>
      Em uma emergência médica, procure atendimento
      imediatamente.
    </p>

    <strong>192</strong>

    <button
      class="botao-principal"
      onclick="ligar()">

      📞 Ligar para o SAMU

    </button>

  </div>

</section>

</main>


<!-- MENU -->

<nav class="menu">

  <button
    class="menu-item ativo"
    onclick="abrir('inicio')">

    <div>⌂</div>
    Início

  </button>


  <button
    class="menu-item"
    onclick="abrir('pesquisa')">

    <div>🔎</div>
    Pesquisar

  </button>


  <button
    class="menu-item"
    onclick="mostrarFavoritos()">

    <div>♡</div>
    Favoritos

  </button>


  <button
    class="menu-item"
    onclick="abrir('perfil')">

    <div>👤</div>
    Perfil

  </button>

</nav>


<script>

const dados = [

  {
    id:"febre",
    nome:"Febre",
    categoria:"Sintomas",
    emoji:"🌡️",
    texto:"A febre é uma elevação da temperatura corporal e pode estar relacionada a infecções."
  },

  {
    id:"dor",
    nome:"Dor de cabeça",
    categoria:"Sintomas",
    emoji:"🤕",
    texto:"A dor de cabeça pode ter diferentes causas e pode aparecer acompanhada de outros sintomas."
  },

  {
    id:"gripe",
    nome:"Gripe",
    categoria:"Sintomas",
    emoji:"🤧",
    texto:"A gripe pode apresentar febre, tosse, dor no corpo, cansaço e mal-estar."
  },

  {
    id:"ansiedade",
    nome:"Ansiedade",
    categoria:"Saúde mental",
    emoji:"🧠",
    texto:"A ansiedade pode envolver preocupação, tensão e sintomas físicos."
  },

  {
    id:"alimentacao",
    nome:"Alimentação saudável",
    categoria:"Nutrição",
    emoji:"🥗",
    texto:"Uma alimentação equilibrada envolve variedade, qualidade dos alimentos e bons hábitos."
  },

  {
    id:"primeiros",
    nome:"Primeiros socorros",
    categoria:"Primeiros socorros",
    emoji:"🩹",
    texto:"Em uma emergência, mantenha a calma, avalie a situação e procure ajuda adequada."
  }

];


let favoritos =
  JSON.parse(localStorage.getItem("favoritos")) || [];


/* ABRIR */

function abrir(id){

  document
    .querySelectorAll(".pagina")
    .forEach(function(p){
      p.classList.remove("ativa");
    });


  const pagina =
    document.getElementById(id);


  if(pagina){

    pagina.classList.add("ativa");

    window.scrollTo(0,0);

  }


  if(id === "favoritos"){
    mostrarFavoritos();
  }


  if(id === "perfil"){
    mostrarPerfil();
  }

}


/* PESQUISA */

function pesquisar(){

  const texto =
    document
    .getElementById("busca")
    .value
    .trim();


  if(texto === ""){

    alert("Digite algo para pesquisar.");

    return;

  }


  abrir("pesquisa");


  document
    .getElementById("busca2")
    .value = texto;


  pesquisar2();

}


function pesquisar2(){

  const texto =
    document
    .getElementById("busca2")
    .value
    .toLowerCase()
    .trim();


  const area =
    document.getElementById("resultadoPesquisa");


  if(texto === ""){

    area.innerHTML = `
      <div class="resultado">
        <h3>🔎 Digite alguma coisa</h3>
        <p>Pesquise por febre, gripe, ansiedade...</p>
      </div>
    `;

    return;

  }


  const encontrados =
    dados.filter(function(item){

      return(
        item.nome.toLowerCase().includes(texto) ||
        item.categoria.toLowerCase().includes(texto) ||
        item.texto.toLowerCase().includes(texto)
      );

    });


  if(encontrados.length === 0){

    area.innerHTML = `
      <div class="resultado">
        <h3>😕 Nada encontrado</h3>
        <p>
          Não encontramos informações sobre "${texto}".
        </p>
      </div>
    `;

    return;

  }


  area.innerHTML = "";


  encontrados.forEach(function(item){

    area.innerHTML += card(item);

  });

}


/* CARD */

function card(item){

  const favorito =
    favoritos.includes(item.id);


  return `

    <div class="resultado">

      <button
        class="favorito-btn"
        onclick="favoritar('${item.id}')">

        ${favorito ? "❤️" : "♡"}

      </button>


      <h3>
        ${item.emoji} ${item.nome}
      </h3>


      <p>
        <strong>${item.categoria}</strong>
      </p>


      <p>
        ${item.texto}
      </p>

    </div>

  `;

}


/* CATEGORIA */

function categoria(nome){

  abrir("categoriaPagina");


  const area =
    document.getElementById("categoriaConteudo");


  const encontrados =
    dados.filter(function(item){

      return item.categoria === nome;

    });


  let html = `
    <h2>${nome}</h2>

    <p class="subtitulo">
      Conteúdos disponíveis nesta categoria.
    </p>
  `;


  encontrados.forEach(function(item){

    html += card(item);

  });


  area.innerHTML = html;

}


/* FAVORITAR */

function favoritar(id){

  const posicao =
    favoritos.indexOf(id);


  if(posicao >= 0){

    favoritos.splice(posicao,1);

  }else{

    favoritos.push(id);

  }


  localStorage.setItem(
    "favoritos",
    JSON.stringify(favoritos)
  );


  if(
    document
    .getElementById("pesquisa")
    .classList
    .contains("ativa")
  ){

    pesquisar2();

  }

}


/* FAVORITOS */

function mostrarFavoritos(){

  abrir("favoritos");


  const area =
    document.getElementById("listaFavoritos");


  if(favoritos.length === 0){

    area.innerHTML = `
      <div class="resultado">
        <h3>♡ Nenhum favorito ainda</h3>
        <p>
          Toque no coração de um conteúdo para salvá-lo.
        </p>
      </div>
    `;

    return;

  }


  area.innerHTML = "";


  favoritos.forEach(function(id){

    const item =
      dados.find(function(x){

        return x.id === id;

      });


    if(item){

      area.innerHTML += card(item);

    }

  });

}


/* PERFIL */

function criarPerfil(){

  const nome =
    document.getElementById("nome").value.trim();

  const email =
    document.getElementById("email").value.trim();


  if(nome === "" || email === ""){

    alert("Preencha nome e e-mail.");

    return;

  }


  const perfil = {

    nome:nome,
    email:email

  };


  localStorage.setItem(
    "perfil",
    JSON.stringify(perfil)
  );


  document.getElementById("saudacao").innerHTML =
    "Olá, " + nome + "! 👋";


  alert("Perfil criado com sucesso! 🎉");


  abrir("inicio");

}


function mostrarPerfil(){

  const area =
    document.getElementById("perfilAtual");


  const perfil =
    JSON.parse(
      localStorage.getItem("perfil")
    );


  if(!perfil){

    area.innerHTML = `
      <h3>👋 Crie seu perfil</h3>
      <p style="margin-top:8px;">
        Personalize sua experiência no VivaSaúde.
      </p>
    `;

    return;

  }


  area.innerHTML = `

    <h3>
      👋 Olá, ${perfil.nome}!
    </h3>

    <p style="margin-top:8px;">
      ${perfil.email}
    </p>

    <p style="margin-top:12px;">
      Seu perfil está salvo neste dispositivo.
    </p>

  `;

}


/* SAMU */

function ligar(){

  window.location.href =
    "tel:192";

}


/* ENTER NA PESQUISA */

document
  .getElementById("busca")
  .addEventListener("keydown",function(e){

    if(e.key === "Enter"){
      pesquisar();
    }

  });


document
  .getElementById("busca2")
  .addEventListener("keydown",function(e){

    if(e.key === "Enter"){
      pesquisar2();
    }

  });


/* PERFIL SALVO */

const perfilSalvo =
  JSON.parse(
    localStorage.getItem("perfil")
  );


if(perfilSalvo){

  document.getElementById("saudacao").innerHTML =
    "Olá, " + perfilSalvo.nome + "! 👋";

}


mostrarPerfil();

</script>

</body>
</>html
