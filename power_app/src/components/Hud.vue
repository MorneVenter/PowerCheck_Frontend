<template>
  <div class = "mainhud">
    <div class="card" style="
    width: 18rem;
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
    margin: auto;
    transition: 0.3s;">
      <img class="card-img-top" src="../assets/back_banner.png" alt="Card image cap">
      <div class="card-body">
        <h5 class="card-title"><b>Morne</b></h5>
        <p class="card-text myText">{{formatData(morne_units)}}</p>
        <a href="#" class="btn btn-danger" @click="getDataMorne">Refresh</a>
      </div>
    </div>

    <div class="card" style="
    width: 18rem;
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
    margin: auto;
    margin-top: 10px;
    transition: 0.3s;">
      <img class="card-img-top" src="../assets/back_banner_2.png" alt="Card image cap">
      <div class="card-body">
        <h5 class="card-title"><b>Arno</b></h5>
        <p class="card-text myText">{{formatData(arno_units)}}</p>
        <a href="#" class="btn btn-dark" @click="getDataArno">Refresh</a>
      </div>
    </div>
</div>
</template>

<script>
  import axios from 'axios';
  export default {
    name: 'Hud',
    data() {
      return {
        arno_units : "Loading ... ",
        morne_units : "Loading ... "
      };
    },
    created: function() {
      this.getDataArno();
      this.getDataMorne();
    },
    methods: {
        getDataMorne() {
          this.morne_units = "Loading ...";
          axios
            .get('https://51.136.30.25:3000/morne')
            .then(res => {
              this.morne_units = res.data[0];
            })
        },
        getDataArno() {
          this.arno_units = "Loading ...";
          axios
            .get('https://51.136.30.25:3000/arno')
            .then(res => {
              this.arno_units = res.data[0];
            });
        },
        formatData(data) {
          if(data === "Loading ...")
            return "Loading ...";
          else
          return data.slice(0, data.indexOf('KWH')+3);
        }
    }
  }
</script>

<style>
  h3 {
    margin-bottom: 5%;
  }
  .myText {
    font-size: 26px;
  }
</style>
