<template>
    <div class="container" >
        <!-- Bootstrap row wrapper div -->
        <div class="row">
            <div class="col-5" style="max-height: 90vh; overflow: scroll">
                <div class="list-group">
                    <router-link v-for="(country,index) in countries" class="list-group-item list-group-item-action" :to="`/list/${country.alpha3Code}`">
                        <img :src="'https://flagpedia.net/data/flags/icon/72x54/' + country.alpha2Code.toLowerCase()+ '.png'" />
                        <p>{{country.name.common}}</p>
                    </router-link>
                  
                </div>
            </div>

            <router-view />
        </div>
    </div>
</template>

<script>
import countries from "../assets/countries.json"

export default {
    data(){
        return{
            countries: countries
        }
    }

}</script>