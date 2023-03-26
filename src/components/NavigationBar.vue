<template>
    <div>
      <div class="topnav">
  <a class="active" href="/ ">Início</a>
  <button v-b-toggle.sidebar-1 class="botaoperfil">Meu Perfil</button>
 
  
</div>


<b-sidebar id="sidebar-1" title="Administrador" shadow>
      <div class="px-3 py-2">
        <p>
          Bem vindo ADM.
        </p>
        <b-img src="https://picsum.photos/500/500/?image=54" fluid thumbnail></b-img>
      </div>
    </b-sidebar>



    </div>
  </template>
  
  <script>
  export default {
    name: 'NavigationBar',
  }
  </script>
  
  <style scoped>
    .navbar-custom {
      box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.9);
      width: 100%;
      left: 0;
      top: 0;
      position: fixed;
      
    }



    /* Add a black background color to the top navigation */
.topnav {
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.9);
      width: 100%;
      left: 0;
      top: 0;
      position: fixed;
  background-color: #070617;;
  overflow: hidden;
}

/* Style the links inside the navigation bar */
.topnav a {
  float: left;
  color: #f2f2f2;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 17px;
}

/* Change the color of links on hover */
.topnav a:hover {
  background-color: #ddd;
  color: black;
}

/* Add a color to the active/current link */
.topnav a.active {
  background-color: #070617;
  color: white;
}

.topnav a:hover{
  background-color: #ddd;
  color: black;
}

.botaoperfil{
  float: left;
  color: #ffffff;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 17px;
  background-color: #070617;
}


.botaoperfil a {
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 17px;
  float: left;
  align-items: center;
  justify-content: center;
}

.botaoperfil a:hover {
  background-color: #ffffff;
}







  </style>
  