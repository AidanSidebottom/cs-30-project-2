<script setup>
  import{ref, computed} from 'vue'

  const directions = [

  {
    direction: "left",
    keyCode: 37,
    move: {
      x: -1,
      y: 0
    }
  },
  {
    direction: "up",
    keyCode: 38,
    move: {
      x: 0,
      y: -1
    }
  },
  {
    direction: "right",
    keyCode: 39,
    move: {
      x: 1,
      y: 0
    }
  },
  {
    direction: "down",
    keyCode: 40,
    move: {
      x: 0,
      y: 1
    }
  }
]

  const f = {name:"food",color:"red",icon:"../src/assets/apple.png"}
  const h ={name:"head",color:"blue",icon:"../src/assets/head_down.png"}
  const b = {name:"body",color:"blue",icon:"../src/assets/body_horizontal.png"}
  const t ={name:"tail",color:"blue",icon:"../src/assets/tail_down.png"}  
  
  let area = ref([
  
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','',h,'','',f,'','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],

])

let snake = [h]
let direction = right

const tiles = (x,y)=>{
if((x+y)%2==0){
    return 'white';
  }
  else{
    return 'black';
  }
}


let started = false

let start = (x,y) =>{
  started=true;
  setTimeout(move(x,y),1000)
  }


let move = (x,y) => {
  
  while (started === true) {
  
  let temp = area.value[x][y]
  area.value[x][y] === ''
  area.value[x+1][y+1] === temp

  }
  start(x,y)
}



</script>

<template>
  <div class="title">
    
    
    
  </div>
 <main class="area">
      <div
        
        v-for="(row, x) in area"
        :key="x"
      >
        <div 
          v-for="(cell, y) in row"
          :key="y"
          v-on:click=start(x,y)
          v-bind:class="tiles(x,y)"
        >
                    
       <img
        v-bind:src="area[x][y].icon"
        v-bind:class="icon"
        >
            
          
        </div>
      </div>
    </main>
    <button v-on:click=start(3,4)>
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
.icon{
}
</style>