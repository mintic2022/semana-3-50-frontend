<template>
  <div class="container-fluid">
    <h1> Bienvenido!, para acceder por favor ingresar su correo y contraseña</h1>
    <br>
    <div class="row">
      <div class="col-5 container">
        <img class="img-fluid"
        src="https://img.freepik.com/foto-gratis/mujer-negocios-que-trabajan-computadora-portatil_1388-67.jpg?size=626&ext=jpg" alt="placeholder">
      </div>
      <div class="col-6">
        <br>
        <form>
          <div class="form-group row ">
            <label for="inputEmail3" class="col-sm-2 col-form-label"
              >Correo</label
            >
            <div class="col-sm-10">
              <input
                class="form-control"
                type="email"
                id="exampleInputEmail1"
                aria-describedby="emailHelp"
                v-model="login.email"
                
              />
            </div>
          </div>
          <br>
          <div class="form-group row">
            <label for="inputPassword3" class="col-sm-2 col-form-label"
              >Contraseña</label
            >
            <div class="col-sm-10">
              <input
                type="password"
                class="form-control"
                id="exampleInputPassword1"
                v-model="login.password"
                
              />
            </div>
          </div>
          <div class="form-group row">
            <div class="col-sm-2"></div>
            <div class="col-sm-10">
              <br>
              <div class="row">
                <div class ="col-md"> 

                  <button type="submit" class="btn btn-primary btn-lg"
                
            
                    @click.prevent="loginUser">INGRESAR</button>
                </div>
                
              </div>
            </div>
          </div>
          
        </form>
        

        
      </div>
    </div>
    <footer class="page-footer font-small blue pt-4">
    <br>
    <br>
  <!-- Footer team -->
  <div class="container-fluid text-center text-md-left">

    <!-- Grid row -->
    <div class="row">

      <!-- Grid column -->
      <div class="col-md-6 mt-md-0 mt-3">

        <!-- Content -->
        <h5 class="text-uppercase">¿Quienes somos?</h5>
        <p>Somos el grupo 50 de la mision tic 2022 , gracias por visitar nuestra pagina esperamos que disfrute su estadia

        </p>

      </div>
      <!-- Grid column -->

      <hr class="clearfix w-100 d-md-none pb-3">

      <!-- Grid column -->
      <div class="col-md-6  mb-md-0 mb-3">

        
        <h5 class="text-uppercase">Miembros</h5>

        <ul class="list-unstyled">
          <li>
            <span>Jonathan Freyberth Pabon: </span><span>freyberth_96@hotmail.com</span>
           
          </li>
          <br>
          <li>
             <span>Jose Luis Muñoz Betancur: </span><span>Dlufyace@gmail.com</span>
          </li>
          <br>
          <li>
            <span>Néstor Manosalva Barrera: </span><span>nemanosalvab@unal.edu.co</span>
          </li>
          <br>
          <li>
            <span>Fabian Diaz: </span><span>fasadif@yahoo.com</span>
            
          </li>
          <br>
          <li>
            <span>Jefferson Andrés Espejo Goez: </span><span>jeaespejogo@unal.edu.co</span>
          </li>
        </ul>

      </div>
      <!--  Grid column -->
 
      
      

    </div>
    <!-- Grid row --></div>
  <!-- Footer team -->
  <br>
  <!-- Declaracion copy -->
  <div class="footer-copyright text-center py-3">© 2020 Copyright: Colombia mintic-2022
    
  </div>
  <!-- Declaracion copy -->

</footer>
<!-- Footer -->
  </div>
</template>

<script>
import swal from "sweetalert";
import VueJwtDecode from "vue-jwt-decode";



export default {

  data() {
    return {
      login:{
                email:"",
                password:""
            }
      
    }
  },
  methods: {
    async loginUser() {
      
      //metodo que llama a la api
      try {
           
            let response = await this.$http.post('/api/auth/signin', this.login);
            // let response = await this.$http.post('/api/users/login',this.login);
           // let response = await axios.post('https://glacial-everglades-74306.herokuapp.com/api/usuario/login',this.login)
            
             let token = response.data.accessToken;
            //  console.log(token);
             let user =  'Pedro';
            //  let email = user.email;
            //  let nombre = user.name;
             

             
             
              // localStorage.setItem('usuario',JSON.stringify(user));
             localStorage.setItem('jwt',token);
             localStorage.setItem('usuario',user);
             if (token){
                  swal("Login successfull", "Bienvenido!", "success")
                this.$router.push('/home');
    }
  }
         
          
         
        
       catch (error) {
        swal("NO coinciden!", "Vuelve a intentarlo", "error");
        console.log(error);
      }
    },
  },
};
</script>
<style>



</style>