<template>
  <div class="list">
    <article v-for="item in pokemon" :key="item" @click="showdetails(item)">
      <h3>
      {{ item.name }}
    </h3>
    <img :src="img_url+item.name+'.png'" alt="">
    </article>
  </div>
</template>

<script>
import axios from 'axios';
import config from '../config/config.json';
export default {
  data:() => {
    return {
      pokemon: [],
      img_url: config.IMG_URL
    }
  },
  mounted(){
    axios.get(config.API_URL+'/pokemon/?offset=20&limit=150').then((response)=>{
      this.pokemon = response.data.results
    })
  },
  methods: {
    showdetails(pokemon){
      //console.log(pokemon)
      this.$emit("showDetails", pokemon)
    }
  }
};
</script>

<style lang="scss" scoped>
.list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  grid-gap: 10px;
  width: 100%;
  max-width: 510px;
}
article {
  height: 150px;
  background-color: #efefef;
  text-align: center;
  text-transform: capitalize;
  border-radius: 5px;
  cursor: pointer;
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2), 0 10px 10px rgba(0, 0, 0, 0.2);
}
h3 {
  margin: 0;
}
#scroll-trigger {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 150px;
  font-size: 2rem;
  color: #efefef;
}

img {
  width: 96px;
  height: 96px;
}
</style>