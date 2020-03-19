<template>
  <div class="container">
    <div class="row search">
        <input type="text" v-model="search" placeholder="Search country.." class="form-control" style="width:500px;"/>
        <select v-model="selected" class="form-control" style="width:200px;margin-left:auto">
            <option disabled value="">Please select region</option>
            <option>A</option>
            <option>B</option>
            <option>C</option>
        </select>
    </div>
    <div class="row">
        <country v-for="country in searchCountries(countries)" v-bind:key="country.name" v-bind:country="country"></country>
    </div>
  </div>
</template>

<script>
    import Country from '../components/Country.vue';
    import axios from "axios";
    export default {
        name: 'home',
        components: {
            Country,
            Letter,
        },
        data () {
            return {
                countries: [],
                search: '',
                region: '',
                selected: [],
            }
        },
        methods: {
            filterByLetter(letter) {
                this.currentLetter = letter;
                
            },
            
            searchCountries(countries) {
                axios.get('https://restcountries.eu/rest/v2/all')
                .then(response => {
                    this.countries = response.data;
                })
                .catch(error => {console.log(error)});
                if(this.search === ''){
                    return this.countries;
                }
                return countries.filter(country => {
                    return country.name.toLowerCase().includes(this.search.toLowerCase());
                })
            },

            filterRegion(countries) {
                axios.get('https://restcountries.eu/rest/v2/all')
                .then(response => {
                    this.countries = response.data;
                })
                .catch(error => {console.log(error)});
                if(this.currentLetter === ''){
                    return this.countries;
                }
                return countries.filter(country => {
                    return country.name.charAt(0).toLowerCase() === this.currentLetter.toLowerCase();
                })
            },

            filterAfrica(countries) {
                axios
                    .get(`https://restcountries.eu/rest/v2/region/africa`)
                    .then(response => {
                        this.countries = response.data;
                    })
                .catch(error => {console.log(error)});
                if(this.region === 'africa'){
                    return this.countries;
                }
                return countries.filter(country => {
                    return country.region.toLowerCase().includes(this.region.toLowerCase());
                })
            },

        },
        
        computed:{

        }
    }
    
</script>

<style scoped>
    .home{
        margin: 50px 100px;
    }
    .search{
        padding: 10px;
    }
</style>