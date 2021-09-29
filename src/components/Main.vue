<template>
  <main class="ps-5 pe-5">

    <section class="container p-5 ">

      <div class="row p-5">

        <div v-for="(element, index) in albumList" :key='index' class="m-3 col-2 ms_album-box">
          
          <AlbumBox :album="element"/>

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
      albumList : []
    }
  },

  created: function () {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then ((answer) => {
      this.albumList = [...answer.data.response];
      console.log(this.albumList)
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../style/variables.scss';

main{

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

}
</style>
