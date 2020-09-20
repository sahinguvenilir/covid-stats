<template>
    <div class="search">
        <input v type="text" v-model="query" @keypress.enter="handleSearch" placeholder="search country"/>
        <button v-on:click="handleSearch">Search</button>
    </div>
</template>

    <script>
        export default {
data () {
    return {
query: ''
    }
},
methods:  {

    handleSearch () {

        this.$emit('SearchRequested', this.query);

        console.log(this.query);
    }
}

        }
        </script>