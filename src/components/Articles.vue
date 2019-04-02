<template>
    <div class="col-4">
        <img v-bind:src="data.urlToImage" class="w-100" v-bind:alt="data.title">
        <h4>{{ data.title }}</h4>
        <h6>{{ data.author}} | {{ data.source.name }}</h6>
        <p>{{ data.description }}</p>
    </div>
</template>

<script>
    export default{
        props: ['data']
    }
</script>

<style>

</style>