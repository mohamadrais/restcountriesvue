<template>
    <div class="card">
        <img class="card-img-top" v-bind:src="aCountry.flag" alt="Card image cap">
        <div class="card-body"  >
            <h4 class="card-title">{{aCountry.name}}</h4>
            <h6 class="card-text">Papulation: <span class="light-text">{{aCountry.population}}</span></h6>
            <h6 class="card-text">Region: <span class="light-text">{{aCountry.region}}</span></h6>
            <h6 class="card-text">Capital: <span class="light-text">{{aCountry.capital}}</span></h6>
            <a href="#" class="btn btn-primary">
                <router-link :to="'/countries/'+country.name+'/info'" class="details-container">
                    <span class="details-text">View More</span><i class="material-icons">open_in_new</i>
                </router-link>
            </a>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Country",

        props: {
            country: {
                type: Object
            }
        },

        data(){
            return {
                aCountry: this.$props.country
            }
        }
    }
</script>

<style scoped>
    .card{
        margin: 10px;
        width: 18rem;
    }
    .card-title{
        font-weight: 800;
    }
    .card-text{
        font-weight: 500;
    }
    .light-text{
        font-weight: 100;
        color: #888888;
    }
    .details-container{
        display: flex;
        justify-content: center;
        color: white;
        text-decoration: none;
        outline: none;
    }
</style>