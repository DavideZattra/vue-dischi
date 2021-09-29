<template>
    
    <div class="ms_album text-center">
        <img class="img-fluid pt-2 pb-2" :src="album.poster" :alt="album.title">
        <h5>{{album.title}}</h5>
        <p>{{album.author}}</p>
        <p>{{album.year}}</p>
    </div>

</template>

<script>
export default {
    name: 'Album',
    props: ["album"],
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

.ms_album{
    h5{
        color: $albumTitleColor;
    }
    p{
        margin: 0;
        color:  $subtitleColor;
    }
}

</style>