<script setup>
  import{ref, computed, VueElement} from 'vue'

  

  const f = {name:"food",color:"red",icon:"./src/assets/apple.png"}
  const h ={name:"head",color:"blue",icon:"./src/assets/head_down.png"}
  const b = {name:"body",color:"blue",icon:"./src/assets/body_horizontal.png"}
  const t ={name:"tail",color:"blue",icon:"./src/assets/tail_down.png"}  
  
  let area = ref([
  
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','',h,'','','','','',''],
  ['','','','',h,'','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],

])

let snake = [ {x: 4, y: 4} , {x: 3, y: 3}]

let randFood = () =>{

  let x = Math.floor(Math.random()*8)
  let y = Math.floor(Math.random()*8)

  area.value[x][y]=f

}


const tiles = (x,y)=>{
if((x+y)%2==0){
    return 'white';
  }
  else{
    return 'black';
  }
}



let started = false

let start = (direction) =>{
  started=true;
  move(direction)
  }


  let move = (direction) => {
    randFood()
    
  
  for (let i = 0; i <= snake.length; i++) {

  let x = snake[i].x
  let y = snake[i].y

  let temp = area.value[x][y]
  area.value[x][y]= ''

  if(direction === 1){

  area.value[x+1][y] = temp
  snake[i].x = snake[i].x+1
  if(i===snake.length){return}
    
  } 

    if(direction === 2){
  area.value[x-1][y] = temp
  snake[0].x = snake[0].x-1
  if(i===snake.length){return}
  } 

    if(direction === 3){
  area.value[x][y+1] = temp
  snake[0].y = snake[0].y+1
  if(i===snake.length){return}
  } 

    if(direction === 4){
  area.value[x][y-1] = temp
  snake[0].y = snake[0].y-1
  if(i===snake.length){return}
  
    } 
    } 
  }

  
  



</script>

<template>
  <div class="title">
    
    
    
  </div>
 <main class="area">
      <div
        
        v-for="(row, y) in area"
        :key="y"
      >
        <div 
          v-for="(cell, x) in row"
          :key="x"
          v-bind:class="tiles(x,y)"
        >
                    
       <img
        v-bind:src="area[x][y].icon"
        >
            
          
        </div>
      </div>
    </main>
    <button v-on:click=start(1)>
      right
    </button>
    <button v-on:click=start(2)>
      left
    </button>
    <button v-on:click=start(3)>
      down
    </button>
    <button v-on:click=start(4)>
      up
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


</style>