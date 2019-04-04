<template>
    <div class="container-fluid">
        <div class="row">
            <div class="col-12 pt-2" id="search">
                <input type="text" placeholder="SEARCH" 
                v-model="searchQ"
                @change.lazy="changeNews">
                <!-- <button v-on:click="changeNews">Submit</button> -->
                <p>{{ searchQ }}</p>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data: function() {
            return {
                searchQ: ''
            }
        },
        methods: {
            changeNews() {
                this.$emit("newsChanged", this.searchQ);
                this.searchQ = '';
            }
        }
    }
</script>

<style>
#search{
    text-align: left;
    background-color: rgb(146, 223, 197);
}
input{
    margin-left: 1%;
}
</style>