<script setup>
  import{ref, computed} from 'vue'

  let currentMove = true;
  
  const f = {name:"food",color:"red",image:"./assets/apple.png"}
  const h ={name:"head",color:"blue",image:".assets/apple.png"}
  const b = {name:"body",color:"blue",image:"b"}
  const t ={name:"tail",color:"blue",image:"t"}  

  const area = ref([
  
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['',b,b,h,'','',f,'','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],

])

const tiles = (x,y)=>{
if((x+y)%2==0){
    return 'white';
  }
  else{
    return 'black';
  }
}

let rightPeice = () =>{
area[x][y].value.name==='food'
}


let start = () =>{
  alert("the game has started")
}


</script>

<template>
  <div class="title">
    Snake
  </div>
 <main class="area">
      <div
        
        v-for="(row, x) in area"
        :key="x"
      >
        <div 
          v-for="(cell, y) in row"
          :key="y"
          
          v-bind:class="tiles(x,y)"
        >
        <div v-if="!area[x][y]">
        </div>
        <div v-else-if="area[x][y].name==='food'">
          <img src="./assets/apple.png">
        </div>
        <div v-else-if="area[x][y].name==='head'">
          <img src="./assets/head_right.png">
        </div>
        <div v-else-if="area[x][y].name==='body'">
          <img src="./assets/body_horizontal.png">
        </div>
            
          
        </div>
        
      </div>
    </main>
    <button v-on:click=start()>
      start
    </button>
</template>

<style scoped>
  .area{
  margin: auto;
  width: 100%;
  
  }
  .white{
  display:inline-block;
  vertical-align:middle;
  
  
  height:40px;
  width:40px;
  background-color: rgb(37, 202, 111);
  padding:10px;
}
.black{
  display:inline-block;
  vertical-align:middle;
  
  
  height:40px;
  width:40px;
  background-color: rgb(12, 117, 61);
  padding:10px;
  
}
.title{
  font-size: 25px;
  padding-bottom: 15px;
  
}
.apple{
  src: "./assets/apple.png";
}
</style>