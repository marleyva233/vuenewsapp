<template>
    <div class="col-4">
        <h6>{{ data.title }}</h6>
        <a v-bind:href="data.url" target="_blank">
            <img v-bind:src="data.urlToImage" class="w-100" v-bind:alt="data.title">
        </a>
        <p>{{ data.author}} | {{ data.source.name }}</p>
        <p>
            {{ data.description }}
            <a v-bind:href="data.url" target="_blank">read article</a>
            <br>
            Published : {{ data.publishedAt }}
        </p>
    </div>
</template>

<script>
    export default{
        props: ['data']
    }
</script>

<style>
.col-4 {
  border: 1px solid #000;
  /*margin: 5px;*/
  padding-top: 3px;
}
</style>