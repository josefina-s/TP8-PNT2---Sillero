<template>

  <section class="src-componentes-tabla">
    <div class="jumbotron">
      <h2>Usuarios Ingresados</h2>
      <br>

      <div v-if="this.$store.state.usuarios.length" class="table-responsive">
        <table class="table table-dark">
          <tr>
            <th>Nombre</th>
            <th>Edad</th>
            <th>Email</th>

          </tr>
          <tr v-for="(usuario,index) in this.$store.state.usuarios" :key="index">
                   <td>{{ usuario.nombre }}</td>
                  <td>{{ usuario.edad }}</td>
                  <td>{{ usuario.email }}</td>
                
              </tr>
        </table>
      </div>
      <h4 v-else class="alert alert-warning text-center">No hay usuarios disponibles</h4>

    </div>
  </section>

</template>

<script>

  export default  {
    name: 'src-componentes-tabla',
    props: [],
    mounted () {

    },
    created () {
      this.getUsuarios()
    },
    data () {
      return {
        url: 'https://633f79d2e44b83bc73bae575.mockapi.io/usuarios',
      }
    },
    methods: {
      async getUsuarios(){
        this.$store.dispatch('getUsuarios')
      }
    },
    computed: {

    }
}

</script>

<style scoped lang="css">
  .jumbotron {
    background-color: #bdf8cf;
    font-family: 'Fira Sans', sans-serif;
  }
</style>
