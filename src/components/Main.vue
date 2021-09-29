<template>
  <main class="ps-5 pe-5">

    <section class="container p-5">

      <div v-if="visualize" class="row p-5">

        <div  v-for="(element, index) in albumList" :key='index' class="m-3 col-2 ms_album-box">
          
          <AlbumBox :album="element"/>

        </div>

        <div></div>

      </div>

      <div v-else class="row ms_loader">
        <div class="col-12 text-center">
          <h1 class="text-black">LOADING</h1>
          <img src="../assets/img/circle-notch.png" alt="">
        </div>
      </div>
    </section>

  </main>
</template>

<script>
import axios from 'axios';
import AlbumBox from './Album.vue'

export default {
  name: 'Main',
  
  components: {
    AlbumBox,
  },
  

  data: function(){
    return{
      albumList : [],
      visualize : false,
    }
  },

  created: function () {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then ((answer) => {
      this.albumList = [...answer.data.response];
      
    });
    setTimeout(() => {
      this.visualize = true;

    }, 2500);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../style/variables.scss';

@keyframes rotation {
  0%{
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}

main{
  height: calc(100vh - 75px);
  background-color: $mainBgColor;

  .ms_album-box{
    background-color: $albumBgColor;

    h5{
      color: $albumTitleColor;
    }

    p{
      color: $subtitleColor;
    
    }

  }

  .ms_loader{

    

    img{
      height: 150px;
      width: 150px;

      animation-name: rotation;
      animation-duration: 1.25s;
      animation-iteration-count: infinite;
      animation-timing-function: linear;

    }

  }

}
</style>
