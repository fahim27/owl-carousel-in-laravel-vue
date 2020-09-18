<template>
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-md-10">
        <div class="card">
          <div class="card-header text-center"><h2>owl carousel laravel and vue</h2> </div>

          <div class="card-body" v-if="sliders">
            <carousel :items='1' :autoplayTimeout="2000" :autoplay="true" :nav="false" >

              <img v-for="slider in sliders" :src="slider.image" />
              
            </carousel>
          </div>
          <div class="card-footer text-right">
              <h5><i>Fahim Muntasir</i></h5>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import carousel from "vue-owl-carousel";

export default {
  mounted() {
      this.getSlider();
    console.log("Component mounted.");

  },
  data(){

      return {
          sliders:null,
      }
  },
  methods:{
      getSlider(){
        axios.get('/slider')
        .then(resp=>{
            this.sliders=resp.data;
        })
        .catch(error=>{
            console.log(error);
        })
      }
  },
  components: { carousel },
};
</script>
