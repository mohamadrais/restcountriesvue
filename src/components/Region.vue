<template>
    <div id="app">
    <h1>Vue Select - Select All</h1>
    <v-select ref="select" multiple :options="options" v-model="selected"></v-select>
    <button class="btn btn-default" @click="selectAll">Select All</button>
    </div>
</template>

<script>
    Vue.component("v-select", VueSelect.VueSelect);

    new Vue({
    el: "#app",
    data: {
        selected: [],
        options: ["foo", "bar", "baz"]
    },
    methods: {
        selectAll() {
        const select = this.$refs.select;
        select.options.forEach(option => {
            select.select(option);
        });
        
        // bug caused by onAfterSelect
        select.open = false
        }
    }
    });

</script>

<style scoped>
    #app {
  max-width: 35em;
  margin: 1em auto;
}
</style>