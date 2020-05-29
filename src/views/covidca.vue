<template>
    <div class="container">
        <center>
            <h1>{{seleccion}}</h1>
            <div class="input-group mb-3">
                <select v-model="seleccion" class="custom-select" id="inputGroupSelect01">
                    <option disabled value="">Seleccione una opcion</option>
                    <option>CENTRO AMERICA</option>
                    <option>El Salvador</option>
                    <option>Costa Rica</option>
                    <option>Nicaragua</option>
                    <option>Honduras</option>
                    <option>Guatemala</option>
                    <option>Panama</option>
                    <option>Belice</option>
                </select>
            </div>

        <div class="row">
            <div class="card border-danger text-danger bg-dark m-3 col md-6" >
                <div class="card-header"><font-awesome-icon icon="skull-crossbones"/> Muertes</div>
                <div class="card-body row">
                    <div class="col sm-4">
                        <h5 class="card-title">Total</h5>
                        <p class="card-text" v-if="seleccion == 'CENTRO AMERICA'">{{es.deaths + cr.deaths + ni.deaths + hn.deaths + gt.deaths + pn.deaths + bl.deaths}}</p>
                        <p class="card-text" v-if="seleccion == 'El Salvador'">{{es.deaths}}</p>
                        <p class="card-text" v-if="seleccion == 'Costa Rica'">{{cr.deaths}}</p>
                        <p class="card-text" v-if="seleccion == 'Nicaragua'">{{ni.deaths}}</p>
                        <p class="card-text" v-if="seleccion == 'Honduras'">{{hn.deaths}}</p>
                        <p class="card-text" v-if="seleccion == 'Guatemala'">{{gt.deaths}}</p>
                        <p class="card-text" v-if="seleccion == 'Panama'">{{pn.deaths}}</p>
                        <p class="card-text" v-if="seleccion == 'Belice'">{{bl.deaths}}</p>
                    </div>
                    <div class="col sm-4">
                        <h5 class="card-title">Hoy</h5>
                        <p class="card-text" v-if="seleccion == 'CENTRO AMERICA'">{{es.todayDeaths + cr.todayDeaths + ni.todayDeaths + hn.todayDeaths + gt.todayDeaths + pn.todayDeaths + bl.todayDeaths}} <span class="badge badge-secondary">Nuevo</span></p>
                        <p class="card-text" v-if="seleccion == 'El Salvador'">{{es.todayDeaths}} <span class="badge badge-secondary">Nuevo</span></p>
                        <p class="card-text" v-if="seleccion == 'Costa Rica'">{{cr.todayDeaths}} <span class="badge badge-secondary">Nuevo</span></p>
                        <p class="card-text" v-if="seleccion == 'Nicaragua'">{{ni.todayDeaths}} <span class="badge badge-secondary">Nuevo</span></p>
                        <p class="card-text" v-if="seleccion == 'Honduras'">{{hn.todayDeaths}} <span class="badge badge-secondary">Nuevo</span></p>
                        <p class="card-text" v-if="seleccion == 'Guatemala'">{{gt.todayDeaths}} <span class="badge badge-secondary">Nuevo</span></p>
                        <p class="card-text" v-if="seleccion == 'Panama'">{{pn.todayDeaths}} <span class="badge badge-secondary">Nuevo</span></p>
                        <p class="card-text" v-if="seleccion == 'Belice'">{{bl.todayDeaths}} <span class="badge badge-secondary">Nuevo</span></p>
                    </div>
                    
                </div>
            </div>

            <div class="card border-info text-info bg-dark m-3 col md-6" >
                <div class="card-header">Casos</div>
                 <div class="card-body row">
                    <div class="col sm-6">
                        <h5 class="card-title">Total</h5>
                        <p class="card-text" v-if="seleccion == 'CENTRO AMERICA'">{{es.cases + cr.cases + ni.cases + hn.cases + gt.cases + pn.cases + bl.cases}}</p>
                        <p class="card-text" v-if="seleccion == 'El Salvador'">{{es.cases}}</p>
                        <p class="card-text" v-if="seleccion == 'Costa Rica'">{{cr.cases}}</p>
                        <p class="card-text" v-if="seleccion == 'Nicaragua'">{{ni.cases}}</p>
                        <p class="card-text" v-if="seleccion == 'Honduras'">{{hn.cases}}</p>
                        <p class="card-text" v-if="seleccion == 'Guatemala'">{{gt.cases}}</p>
                        <p class="card-text" v-if="seleccion == 'Panama'">{{pn.cases}}</p>
                        <p class="card-text" v-if="seleccion == 'Belice'">{{bl.cases}}</p>
                    </div>
                    <div class="col sm-6">
                        <h5 class="card-title">Activos</h5>
                        <p class="card-text" v-if="seleccion == 'CENTRO AMERICA'">{{es.active + cr.active + ni.active + hn.active + gt.active + pn.active + bl.active}}</p>
                        <p class="card-text" v-if="seleccion == 'El Salvador'">{{es.active}}</p>
                        <p class="card-text" v-if="seleccion == 'Costa Rica'">{{cr.active}}</p>
                        <p class="card-text" v-if="seleccion == 'Nicaragua'">{{ni.active}}</p>
                        <p class="card-text" v-if="seleccion == 'Honduras'">{{hn.active}}</p>
                        <p class="card-text" v-if="seleccion == 'Guatemala'">{{gt.active}}</p>
                        <p class="card-text" v-if="seleccion == 'Panama'">{{pn.active}}</p>
                        <p class="card-text" v-if="seleccion == 'Belice'">{{bl.active}}</p>
                        
                    </div>

                    <div class="col sm-4">
                        <h5 class="card-title">Hoy</h5>
                        <p class="card-text" v-if="seleccion == 'CENTRO AMERICA'">{{es.todayCases + cr.todayCases + ni.todayCases + hn.todayCases + gt.todayCases + pn.todayCases + bl.todayCases}} <span class="badge badge-secondary">Nuevo</span></p>
                        <p class="card-text" v-if="seleccion == 'El Salvador'">{{es.todayCases}} <span class="badge badge-secondary">Nuevo</span></p>
                        <p class="card-text" v-if="seleccion == 'Costa Rica'">{{cr.todayCases}} <span class="badge badge-secondary">Nuevo</span></p>
                        <p class="card-text" v-if="seleccion == 'Nicaragua'">{{ni.todayCases}} <span class="badge badge-secondary">Nuevo</span></p>
                        <p class="card-text" v-if="seleccion == 'Honduras'">{{hn.todayCases}} <span class="badge badge-secondary">Nuevo</span></p>
                        <p class="card-text" v-if="seleccion == 'Guatemala'">{{gt.todayCases}} <span class="badge badge-secondary">Nuevo</span></p>
                        <p class="card-text" v-if="seleccion == 'Panama'">{{pn.todayCases}} <span class="badge badge-secondary">Nuevo</span></p>
                        <p class="card-text" v-if="seleccion == 'Belice'">{{bl.todayCases}} <span class="badge badge-secondary">Nuevo</span></p>
                    </div>
                </div>
            </div>
        </div>
        <div class="row">
            <div class="card border-warning text-warning bg-dark m-3 col md-6" >
                <div class="card-header">Criticos</div>
                <div class="card-body">
                <h5 class="card-title">Todos</h5>
                <p class="card-text" v-if="seleccion == 'CENTRO AMERICA'">{{es.critical + cr.critical + ni.critical + hn.critical + gt.critical + pn.critical + bl.critical}}</p>
                <p class="card-text" v-if="seleccion == 'El Salvador'">{{es.critical}}</p>
                <p class="card-text" v-if="seleccion == 'Costa Rica'">{{cr.critical}}</p>
                <p class="card-text" v-if="seleccion == 'Nicaragua'">{{ni.critical}}</p>
                <p class="card-text" v-if="seleccion == 'Honduras'">{{hn.critical}}</p>
                <p class="card-text" v-if="seleccion == 'Guatemala'">{{gt.critical}}</p>
                <p class="card-text" v-if="seleccion == 'Panama'">{{pn.critical}}</p>
                <p class="card-text" v-if="seleccion == 'Belice'">{{bl.critical}}</p>
                </div>
            </div>

            <div class="card border-success text-success bg-dark m-3 col md-6" >
                <div class="card-header">Recuperados</div>
                <div class="card-body">
                <h5 class="card-title">Todos</h5>
                <p id="m-es" class="card-text" v-if="seleccion == 'CENTRO AMERICA'">{{es.recovered + cr.recovered + ni.recovered + hn.recovered + gt.recovered + pn.recovered + bl.recovered}}</p>
                <p class="card-text" v-if="seleccion == 'El Salvador'">{{es.recovered}}</p>
                <p class="card-text" v-if="seleccion == 'Costa Rica'">{{cr.recovered}}</p>
                <p class="card-text" v-if="seleccion == 'Nicaragua'">{{ni.recovered}}</p>
                <p class="card-text" v-if="seleccion == 'Honduras'">{{hn.recovered}}</p>
                <p class="card-text" v-if="seleccion == 'Guatemala'">{{gt.recovered}}</p>
                <p class="card-text" v-if="seleccion == 'Panama'">{{pn.recovered}}</p>
                <p class="card-text" v-if="seleccion == 'Belice'">{{bl.recovered}}</p>
                </div>
            </div>
        </div>
        </center>
    </div>  
</template>

<script>
import { faChessQueen } from '@fortawesome/free-solid-svg-icons'
import  Bar  from 'vue-chartjs'
import axios from 'axios'
export default {
    data() {
        return {
            seleccion : '',
            es : null,
            cr : null,
            ni : null,
            hn : null,
            gt : null,
            pn : null,
            bl : null
        }
    },

    mounted() {
        this.elsalvador(),
        this.costarica(),
        this.nicaragua(),
        this.honduras(),
        this.guatemala(),
        this.panama(),
        this.belice()
    },

    methods: {
        
        elsalvador(){
            //PETICION GET DE EL SALVADOR
            axios.get('https://coronavirus-19-api.herokuapp.com/countries/el%20salvador')
            .then(res => {
                console.log(res)
                this.elsalvador = res.data
                this.es = res.data
            })
            .catch(err => {
                console.error(err); 
            })
        },

        costarica(){
            //PETICION GET DE EL COSTA RICA
            axios.get('https://coronavirus-19-api.herokuapp.com/countries/costa%20rica')
            .then(res => {
                console.log(res)
                this.costarica = res.data
                this.cr = res.data
            })
            .catch(err => {
                console.error(err); 
            })
        },

        nicaragua(){
            //PETICION GET DE EL NICARAGUA
            axios.get('https://coronavirus-19-api.herokuapp.com/countries/nicaragua')
            .then(res => {
                console.log(res)
                this.nicaragua = res.data
                this.ni = res.data
            })
            .catch(err => {
                console.error(err); 
            })
        },

        honduras(){
            //PETICION GET DE EL HONDURAS
            axios.get('https://coronavirus-19-api.herokuapp.com/countries/honduras')
            .then(res => {
                console.log(res)
                this.honduras = res.data
                this.hn = res.data
            })
            .catch(err => {
                console.error(err); 
            })
        },

        guatemala(){
            //PETICION GET DE EL GUATEMALA
            axios.get('https://coronavirus-19-api.herokuapp.com/countries/guatemala')
            .then(res => {
                console.log(res)
                this.guatemala = res.data
                this.gt = res.data
            })
            .catch(err => {
                console.error(err); 
            })
        },

        panama(){
            //PETICION GET DE EL PANAMA
            axios.get('https://coronavirus-19-api.herokuapp.com/countries/panama')
            .then(res => {
                console.log(res)
                this.panama = res.data
                this.pn = res.data
            })
            .catch(err => {
                console.error(err); 
            })
        },


        belice(){
            //PETICION GET DE EL BELIZE
            axios.get('https://coronavirus-19-api.herokuapp.com/countries/belize')
            .then(res => {
                console.log(res)
                this.belice = res.data
                this.bl = res.data
            })
            .catch(err => {
                console.error(err); 
            })
        },

    },
    
}
</script>