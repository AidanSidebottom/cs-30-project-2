<script setup>
  import{ref, computed} from 'vue'
  let currentMove = true;
  
  const f = {name:"food",color:"red",icon:"../src/assets/apple.png"}
  const h ={name:"head",color:"blue",icon:"../src/assets/head_down.png"}
  const b = {name:"body",color:"blue",icon:"../src/assets/body_horizontal.png"}
  const t ={name:"tail",color:"blue",icon:"../src/assets/tail_down.png"}  
  
  let area = ref([
  
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','',f,'','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],

])

let snake = [h]

const tiles = (x,y)=>{
if((x+y)%2==0){
    return 'white';
  }
  else{
    return 'black';
  }
}

let counter = 0


let start = () =>{
  
  alert("the game has started")
  area.value[counter][1]= f;
  counter++;
  setTimeout(move(),1000)
  
}

let move = () =>{
  alert(" moveing the snake ")
  area.value[4][3]= h;
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
.icon{
}
</style>