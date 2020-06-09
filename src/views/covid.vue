<template>
  <div class="container">
    <center>
      <h3>{{seleccion.nombre}}</h3>
      <select v-model="seleccion" :options="paises" class="form-control">
        <option disabled value>Seleccione una opcion</option>
        <option
          v-for="pais in paises"
          :key="pais.id"
          v-bind:value="{nombre: pais.country, muertes:pais.deaths ,muertesHoy:pais.todayDeaths , casos:pais.cases ,activos:pais.active ,casosHoy:pais.todayCases ,criticos:pais.critical ,recuperados:pais.recovered }"
        >{{pais.country}}</option>
      </select>

      <div class="row">
        <div class="col-sm-12 col-md-6">
          <div class="card border-danger text-danger bg-dark mt-2">
            <div class="card-header">
              <i class="fas fa-skull-crossbones"></i> Muertes
            </div>
            <div class="card-body row">
              <div class="col sm-4">
                <h5 class="card-title">Total</h5>
                <p class="card-text">{{seleccion.muertes}}</p>
              </div>
              <div class="col sm-4">
                <h5 class="card-title">Hoy</h5>
                <p class="card-text">
                  {{seleccion.muertesHoy}}
                  <span class="badge badge-secondary" v-if="seleccion != ''">Nuevo</span>
                </p>
              </div>
            </div>
          </div>
        </div>

        <div class="col-sm-12 col-md-6">
          <div class="card border-info text-info bg-dark mt-2">
            <div class="card-header">
              <i class="fas fa-virus"></i> Casos
            </div>
            <div class="card-body row">
              <div class="col sm-6">
                <h5 class="card-title">Total</h5>
                <p class="card-text">{{seleccion.casos}}</p>
              </div>
              <div class="col sm-6">
                <h5 class="card-title">Activos</h5>
                <p class="card-text">{{seleccion.activos}}</p>
              </div>

              <div class="col sm-4">
                <h5 class="card-title">Hoy</h5>
                <p class="card-text">
                  {{seleccion.casosHoy}}
                  <span class="badge badge-secondary" v-if="seleccion != ''">Nuevo</span>
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="row">
        <div class="col-sm-12 col-md-6">
          <div class="card border-warning text-warning bg-dark mt-2">
            <div class="card-header">
              <i class="fas fa-exclamation-triangle"></i> Criticos
            </div>
            <div class="card-body">
              <h5 class="card-title">Todos</h5>
              <p class="card-text">{{seleccion.criticos}}</p>
            </div>
          </div>
        </div>

        <div class="col-sm-12 col-md-6">
          <div class="card border-success text-success bg-dark mt-2">
            <div class="card-header">
              <i class="fas fa-heartbeat"></i> Recuperados
            </div>
            <div class="card-body">
              <h5 class="card-title">Todos</h5>
              <p id="m-es" class="card-text">{{seleccion.recuperados}}</p>
            </div>
          </div>
        </div>
      </div>

      <div class="mt-3">
        <h3>Grafico de {{seleccion.nombre}}</h3>
        <pie-chart :data="seleccion"></pie-chart>
      </div>
    </center>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      seleccion: "",
      paises: []
    };
  },
  mounted() {
    this.mundo();
  },

  methods: {
    mundo() {
      axios
        .get("https://coronavirus-19-api.herokuapp.com/countries")
        .then(res => {
          console.log(res);
          this.mundo = res.data;
          this.paises = res.data;
        })
        .catch(err => {
          console.error(err);
        });
    }
  }
};
</script>

<style>
.margen-derecho {
  margin-top: 20px;
}
</style>