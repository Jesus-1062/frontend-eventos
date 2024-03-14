<template>
  <v-app-bar app elevate-on-scroll elevation="8" 
  height="152px"
  relative flat class="fondo">
      <v-app-bar-nav-icon
      class="btn"
      dark
      @click="procesa()"
    ></v-app-bar-nav-icon>

    <v-toolbar-title >
      <!-- <div class="letra">
        GESTION DE EVENTOS  
      </div> -->
    
        <img 
          src="../../assets/images/Titulo2.png"
          alt="Evento"
          width="500px"
        >
        <br>
      <div class="nombre">
        Bienvenido : {{usuario}}
      </div>
    
       
    </v-toolbar-title>

    <v-spacer></v-spacer>

    <v-menu offset-y>
      <template v-slot:activator="{ on, attrs }">
        <span v-bind="attrs" v-on="on" style="cursor: point" class="mx-5 mr-10">
          <v-avatar size="40">
            <img src="https://randomuser.me/api/portraits/women/80.jpg" />
          </v-avatar>
        </span>
      </template>
      <v-list dense>
        <v-list-item-group v-model="selectedItem" color="primary">
          <v-list-item v-for="(item, i) in items" :key="i"
           :to="item.link">
            <v-list-item-icon>
              <v-icon v-text="item.icon"></v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title 
               v-text="item.text"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-menu>
  </v-app-bar>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { text: "Perfil", icon: "mdi-clock", link :''},
        { text: "Salir", icon: "mdi-account",link : "/dashboard/salida" },
      ],
    };
  },
  computed: {
    usuario(){
        return `${this.$store.getters.usuario.nombre} ${this.$store.getters.usuario.apellido}`
    }
  },
  methods: {
    procesa() {
      console.log("generado");
      this.$emit("handrawer");
    },
    
  },
};
</script>
<style lang="scss" scoped>
.letra {
  color:black;
  font-size: 40px;
  font-family:'Courier New', Courier, monospace;
  font-weight: 500;
  text-shadow: 2px 2px 3px gray;
}

.fondo{
  background-image: url(../../assets/images/fondotex.png); /* Reemplaza '/ruta/a/la/imagen.jpg' con la ruta de tu imagen */
  
  background-repeat: no-repeat;
  background-size: 100% 100%;
  background-attachment: fixed;
  width: 78%;
  height: 100%;
  margin: 0;
}
.nombre {
  font-family: 'Roboto', sans-serif; /* Cambia 'Roboto' por la tipografía que desees */
}


</style>