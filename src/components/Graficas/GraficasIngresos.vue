<template>
    <v-container grid-list-m>
        <h2 class="text-center primary--text mb-5">Ingresos por meses del ultimo año</h2>
        <v-layout wrap>
            <v-flex xs12 sm12 md12>
                <div>
                    <canvas id="myChart">

                    </canvas>
                </div>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
import axios from 'axios'
import {hart} from 'chart.js'

export default{
    data(){
        return{
            nombreMeses:[],
            mesesValores:null,
            totalMeses:[],
            
        }
    },
    methods:{
        loadProductosMasVendidos(){
            let me=this;
            let mesn='';
            me.mesesValores.map(function(x){
                switch(parseInt(x.nombreMeses)){
                    case 1: mesn='Enero'; break;
                    case 2: mesn='Febrero'; break;
                    case 3: mesn='Marzo'; break;
                    case 4: mesn='Abril'; break;
                    case 5: mesn='Mayo'; break;
                    case 6: mesn='Junio'; break;
                    case 7: mesn='Julio'; break;
                    case 8: mesn='Agosto'; break;
                    case 9: mesn='Septiembre'; break;
                    case 10: mesn='Ocutubre'; break;
                    case 11: mesn='Nomviembre'; break;
                    case 12: mesn='Diciembre'; break;

                }
                me.nombreMeses.push(mesn);
                me.totalMeses.push(x.mesesValores);
            });
            var ctx=document.getElementById("myChart");
            var myChart =new Chart(ctx,{
                type: 'line',
                data:{
                    labels: me.nombreMeses,
                    datasets:[{
                        label: 'Ingresos en los ultimos 12 meses',
                        data: me.totalMeses,
                        backgroundColor:[
                            'rgba(255, 99, 132, 0.2)',
                            'rgba(54, 162, 235, 0.2)',
                            'rgba(255, 206, 86, 0.2)',
                            'rgba(75, 192, 192, 0.2)',
                            'rgba(153, 102, 255, 0.2)',
                            'rgba(255, 159, 64, 0.2)',
                            'rgba(255, 99, 132, 0.2)',
                            'rgba(54, 162, 235, 0.2)',
                            'rgba(255, 206, 86, 0.2)',
                            'rgba(75, 192, 192, 0.2)',
                            'rgba(153, 102, 255, 0.2)',
                            'rgba(255, 159, 64, 0.2)'
                        ],
                        borderColor: [
                            'rgba(255, 99, 132, 1)',
                            'rgba(54, 162, 235, 1)',
                            'rgba(255, 206, 86, 1)',
                            'rgba(75, 192, 192, 1)',
                            'rgba(153, 102, 255, 1)',
                            'rgba(255, 159, 64, 1)',
                            'rgba(255, 99, 132, 1)',
                            'rgba(54, 162, 235, 1)',
                            'rgba(255, 206, 86, 1)',
                            'rgba(75, 192, 192, 1)',
                            'rgba(153, 102, 255, 1)',
                            'rgba(255, 159, 64, 1)'
                        ],
                        borderWidth: 1
                    }]
                },
                options:{
                    scales:{
                        yAxes:[{
                            ticks:{
                                beginAtZero:false
                            }
                        }]
                    }
                }
            });
        },

        getProductosMasVendidos(){
            let me=this;
            axios.get('api/Ingresos/GraficaIngresos').then(function(response){
                me.mesesValores=response.data;
                me.loadProductosMasVendidos();
            }).catch(function(error){
                console.log(error);
            });
            
        }
    },
    mounted(){
        this.getProductosMasVendidos();
    }

}

</script>
