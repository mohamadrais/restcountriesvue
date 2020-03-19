<template>
    <div>
        route id {{id}}
    </div>
</template>

<script>
import axios from "axios";

    export default {
        name: "Info",
        props: ['id'],

        methods: {
            mounted() {
                let countryName = this.$route.params.query;

                axios
                .get(`https://restcountries.eu/rest/v2/name/${countryName}?fullText=true`)
                .then(response => {
                    this.country = response.data;
                });
            },
        },
    }

</script>

<style scoped>

</style>