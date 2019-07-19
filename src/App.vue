<template>
  <div id="app">
    <div class="main">
      <div class="field" v-for="(item, index) of arr" :key="item.id"> <img :src="'./src/assets/'+item.fieldBack" class="field-img" @click="build(index)"></div>
    </div>
    <div class="build-menu" v-if="show">  
      <h3>Что хотите построить?</h3>
      <div class="item-menu">
        <img src="./assets/house1.jpg" class="item-menu__img" @click="buildItem('house1')">
      </div>
      <div class="item-menu">
        <img src="./assets/forest1.jpg" class="item-menu__img" @click="buildItem('forest1')">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      fieldBack: "field1.png",
      arr: [],
      show: false,
      fieldIndex: null
    }
  },
  mounted(){
    for(var i=0; i<100; i++){
      var field={}
      var rand = Math.random()
      if (rand<0.25){
        field.fieldBack = "forest1.jpg" 
      }else{
        field.fieldBack = "field1.png" 
      }
      
      field.id = i
      this.arr.push(field)
    }
  },
  methods:{
    build(value){
      if(this.arr[value].fieldBack === 'field1.png'){
        this.show = true;
        this.fieldIndex = value;
        alert(this.fieldIndex)
      } else 
      if(this.arr[value].fieldBack === 'forest1.jpg'){
        this.arr[value].fieldBack = "field1.png"
      }
      
    },
    buildItem(value){
      alert(this.fieldIndex);
      this.arr[this.fieldIndex].fieldBack = value + ".jpg"
      this.show = false;
    }
  }
}
</script>

<style>
  .main{
    width: 1000px;
    height: 1000px;
  }
  .field-img{
    width: 100%;
  }
  .field-img:hover{
    border: 1px  solid gold;
    cursor: pointer;
  }
  .field{
    width: 100px;
    height: 100px;
    float: left;
  }
  .build-menu{
    position: absolute;
    border: 2px solid black;
    width: 150px;
    top: 50%;
    left: 50%;
    transform: translate(-50%);
    background: black;
    color: aliceblue;
  }
  .item-menu{
    float: left;
    margin: 10px;
    width: 100%;
  }

  .item-menu__img{
    width: 50px;
  }
</style>
