<script setup>
  import{ref, computed} from 'vue'

  let currentMove = true;
  
  const food = {name:"food",color:"red",image:"./assets/apple.png"}
  const head ={name:"head",color:"blue",image:".assets/apple.png"}
  const body = {name:"body",color:"blue",image:"b"}
  const tail ={name:"tail",color:"blue",image:"t"}  

  const area = ref([
  
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','',head,'','',food,'','',''],
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
        <div>
          <img v-bind:src="area[x][y].image">
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