<template>
    <div class="features-container">
        <div class="container">
            <div class="row">
                <div class="col s10">
                    <h4>Features for {{contenent}}</h4>
                </div>
            </div>
            <div class="row">
               <div class="col m4" v-for="(item, index) in cards" :key="index">
                    <div class="card">
                        <div class="card-image">
                            <img :src="'https://picsum.photos/350/225/?random'">
                            <span class="card-title">{{ item.title }}</span>
                            <span class="card-subtitle">{{ item.subtitle }} {{contenent}}</span>
                        </div>
                        <div class="card-content">
                            <p>{{ item.content }}</p>
                        </div>
                        <div class="card-action">
                            <a href="#">more . . .</a>
                        </div>
                    </div>
               </div>
            </div>
        </div>
    </div>    
</template>
<script>
const axios = require('axios');
export default {
    data() {
        return {
            country:"",
            city:"",
            contenent:"",
            cards:[
                {
                    title:"ERP Software",
                    subtitle:"Best ERP in ",
                    content:"Deskera ERP is easy-to-use accounting software that facilitates recording and processing of different financial transactions and processes. "
                }, 
                {
                    title:"MRP Software",
                    subtitle:"Best MRP in ",
                    content:"Deskera MRP solution helps you optimize your entire manufacturing process – from production planning and process scheduling."
                }, 
                {
                    title:"CRM Software",
                    subtitle:"Best CRM in ",
                    content:"Deskera Customer Relationship Management Software provides an organization with a single view of its customers;  "
                }, 
                {
                    title:"HRMS Software",
                    subtitle:"Best HRMS in ",
                    content:"Created by HR professionals, Deskera HRMS gives organizations the much-needed tools to manage their most important asset – the people.  "
                }, 
                {
                    title:"eLeave Software",
                    subtitle:"Best eLeave in ",
                    content:"Looking for a paperless and hassle-free solution for managing employee leaves?  "
                }, 
                {
                    title:"ERP Software",
                    subtitle:"Best ERP in ",
                    content:"Deskera ERP is easy-to-use accounting software that facilitates recording and processing of different financial transactions and processes. "
                }, 
                
            ]
        }
    },methods: {
        getContenent:function() {
            let country = this.country;
            axios.get('https://restcountries.eu/rest/v2/name/' + country).then((response)=> {
            this.contenent = response.data[0].region
        })
        }
    },
    mounted : function() {
        axios.get('http://ip-api.com/json').then((response)=>{
            this.country = response.data.country
            this.city = response.data.city
            this.getContenent();
        })
       
       

    }
}
</script>
<style scoped>
    .features-container {
        min-height: 100vh;
        height: 100%;
        width: 100%;
        padding:25px 0;
        box-sizing: border-box;
        background-color: #f2f1ef !important
    }
    h4 {
        font-family: 'Montserrat', sans-serif;
        color: #d40d12;
        font-weight: 900
    }
    .card-action a{
        color: #d40d12!important;
        
    }
    .card-subtitle {
        position: absolute;
        bottom:10px;
        left: 0;
        padding-left: 24px;
        color: #fff;
    }
</style>

