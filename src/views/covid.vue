<template>
    <div class="container">
        <select v-model="seleccion" :options="paises" class="form-control">
            <option v-for="pais in paises" :key="pais.id" 
            v-bind:value="{nombre: pais.country, muertes:pais.deaths ,muertesHoy:pais.todayDeaths , casos:pais.cases ,activos:pais.active ,casosHoy:pais.todayCases ,criticos:pais.critical ,recuperados:pais.recovered }"
            >{{pais.country}}</option>
        </select>

        <center>
            <div class="row">
            <div class="card border-danger text-danger bg-dark m-3 col md-6" >
                <div class="card-header"><font-awesome-icon icon="skull-crossbones"/> Muertes</div>
                <div class="card-body row">
                    <div class="col sm-4">
                        <h5 class="card-title">Total</h5>
                        <p class="card-text">{{seleccion.muertes}}</p>
                    </div>
                    <div class="col sm-4">
                        <h5 class="card-title">Hoy</h5>
                        <p class="card-text">{{seleccion.muertesHoy}} <span class="badge badge-secondary">Nuevo</span></p>
                    </div>
                    
                </div>
            </div>

            <div class="card border-info text-info bg-dark m-3 col md-6" >
                <div class="card-header">Casos</div>
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
                        <p class="card-text">{{seleccion.casosHoy}} <span class="badge badge-secondary">Nuevo</span></p>
                    </div>
                </div>
            </div>
        </div>
        <div class="row">
            <div class="card border-warning text-warning bg-dark m-3 col md-6" >
                <div class="card-header">Criticos</div>
                <div class="card-body">
                <h5 class="card-title">Todos</h5>
                <p class="card-text">{{seleccion.criticos}}</p>
                </div>
            </div>

            <div class="card border-success text-success bg-dark m-3 col md-6" >
                <div class="card-header">Recuperados</div>
                <div class="card-body">
                <h5 class="card-title">Todos</h5>
                <p id="m-es" class="card-text">{{seleccion.recuperados}}</p>
                </div>
            </div>
        </div>
        </center>
        
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return{
            seleccion:'',
            paises:[]
        }
    },
    mounted() {
        this.mundo()
    },

    methods: {
        mundo(){
            axios.get('https://coronavirus-19-api.herokuapp.com/countries')
            .then(res => {
                console.log(res)
                this.mundo = res.data
                this.paises = res.data

            })
            .catch(err => {
                console.error(err); 
            })
        }
    },
}
</script>