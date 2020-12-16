<template>
  <div class="container-fluid">
    <h1>
      Felicidades {{ user.name }},aqui estan algunos de todas en caso de error
      por favor comunicarse con el administrador
    </h1>
    <br /><br />
    <br />

    <div class="container">
      <div class="row">
        <div class="form"  >
          <ul class="list-group">
            <li class="list-group-item">
              <h2>
                <span text-left>Nombre: </span><span>{{ user.name }}</span>
                <br>
              </h2>
            </li>
            <li class="list-group-item">
              <h2>
                <span>Correo: </span><span>{{ user.email }}</span>
                <br>
              </h2>
            </li>
            <!-- <li class="list-group-item">
              <h2>
                <span>id: </span><span>{{ user.id }}</span>
                <br>
              </h2>
            </li> -->
          </ul>
        </div>
      </div>
    </div>
    <div>
        <br>
<h3 class ="text-justify">para salir y borrar sus datos pulse el boton de salir</h3>    </div>
    <div class="container mt-5">
      <div class="container-fluid">
        <form>
          <button
            class="btn btn-outline-primary btn-lg"
            type="submit"
            @click.prevent="logOutUser"
          >
            Salir
          </button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import VueJwtDecode from "vue-jwt-decode";
export default {
  props: {
    email: String,
  },
  data() {
    return {
      user: {},
    };
  },
  methods: {
    logOutUser() {
      localStorage.removeItem("jwt");
      localStorage.removeItem("usuario");
      this.$router.push("/");
    },
    getUserData() {
      let token = localStorage.getItem("jwt");

      //  let user = localStorage.getItem('usuario');
      // let user =localStorage.getItem('usuario');
      // this.user = JSON.parse(user)
      // console.log(token);

      let decoded = VueJwtDecode.decode(token);
      this.user = decoded;
    },
  },
  created() {
    this.getUserData();
  },
};
</script>