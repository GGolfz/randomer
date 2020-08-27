<template>
  <v-app>
    <v-main>
      <v-container>
        <v-row>
          <v-col cols="12" class="col-center v-title">
            RANDOMER
          </v-col>
          <v-col cols="12" class="col-center itemadd">
          <v-text-field
            v-model="item"
            label="Add Item"
          ></v-text-field>
          </v-col>
          <v-col cols="12" class="col-center">
            <v-btn @click="add()" outlined color="white" large class="button1"> ADD </v-btn>
          </v-col>
          <v-col cols="12" class="col-center">
            Current Data (Click for Remove)
          </v-col>
          <v-col cols="12" class="col-center">
            {{data.length == 0?'Please Add Data before Random':''}}
          </v-col>
          <v-col cols="12" class="col-center">
            <v-row class="datarow">
              <v-col v-for="(i,index) in data" :key="index" @click="remove(index)">
                {{i}}
              </v-col>
            </v-row>
          </v-col>
          <v-col cols="12" class="col-center">
          <v-btn @click="random()" outlined color="white" x-large class="button1">RANDOM</v-btn>
          </v-col>
          <v-col cols="12" class="col-center output">
            {{show}}
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>
<style>
  .v-title {
    font-size: 2.8em;
    margin-bottom: 3%;
    color: white;
    font-weight: bolder;
  }
  .datarow {
    cursor:pointer;
    padding: 0% 10%;
    text-align: center;
    flex:none !important;
  }
  .itemadd {
    padding: 0% 40% !important;
  }
  .container {
    height: 100vh;
    font-family: 'Balsamiq Sans', cursive !important;
    margin:0 !important;
    width:100vw !important;
    max-width: 100vw !important;
    display:flex;
    align-items: center;
    background: rgb(238,174,202);
    background: radial-gradient(circle, rgba(238,174,202,1) 0%, rgba(148,187,233,1) 100%);
  }
  .output {
    font-size: 1.4em !important;
    color: white !important;
  }
  .button1 {
    font-size: 1.4em !important;
  }
  .col-center{ 
    display:flex;
    justify-content: center;
    align-items: center;
  }
  body{
    height: 100vh;
  }
</style>
<script>

export default {
  data: () => ({
    data: [],
    show: '',
    item: ''
  }),
  methods: {
    add() {
      if(this.item != ''){
        this.data.push(this.item)
        this.item = ''
      }
    },
    random(){
      if(this.data.length == 0 ){
        alert("Please add data before using randomer")
      } else{
        let i = 0;
        var x = setInterval(()=>{
          this.show = this.data[Math.floor(Math.random() *this.data.length)]
          i +=1;
          if(i >=30){
            clearInterval(x);
          }
        },100)
      }
    },
    remove(id){
      this.data.splice(id,1);
    }
  },
  mounted() {

  },
};
</script>
