<template>
    <div>
        

    </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
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
        this.belize()
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


        belize(){
            //PETICION GET DE EL BELIZE
            axios.get('https://coronavirus-19-api.herokuapp.com/countries/belize')
            .then(res => {
                console.log(res)
                this.belize = res.data
                this.bl = res.data
            })
            .catch(err => {
                console.error(err); 
            })
        },

    },
}
</script>