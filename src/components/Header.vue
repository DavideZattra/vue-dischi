<template>
    <header>
        <img src="../assets/img/spotify-logo.png" alt="spotify logo">
    </header>
</template>

<script>
export default {
    name : 'Header',
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

header{
    height: 75px;
    background-color: $headerBgColor;
    
    img{
        height: 75px;
    }
}
</style>