<script setup>
  import{ref, computed} from 'vue'

  

  const f = {name:"food",color:"red",icon:"../src/assets/apple.png"}
  const h ={name:"head",color:"blue",icon:"../src/assets/head_down.png"}
  const b = {name:"body",color:"blue",icon:"../src/assets/body_horizontal.png"}
  const t ={name:"tail",color:"blue",icon:"../src/assets/tail_down.png"}  
  
  let area = ref([
  
  ['','','','','','','','','',''],
  ['',h,'','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','',h,'','',f,'','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],

])

let snake = [ {x: 1, y: 1} , ]




const tiles = (x,y)=>{
if((x+y)%2==0){
    return 'white';
  }
  else{
    return 'black';
  }
}


let started = false

let start = (x,y,direction) =>{
  started=true;
  move(x,y,direction)
  alert(snake[0].x)
  }


  let move = (x,y,direction) => {
  
  while (started === true) {
  
  let temp = area.value[x][y]
  area.value[x][y] = ''

  if(direction === 1){
  area.value[x+1][y] = temp
  return
  
    } 
    if(direction === 2){
  area.value[x-1][y] = temp
  return
  
    } 
    if(direction === 3){
  area.value[x][y+1] = temp
  return
  
    } 
    if(direction === 4){
  area.value[x][y-1] = temp
  return
  
    } else{
      alert("invalid direction")
      return
      
    }
    
  }
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
          v-bind:class="tiles(x,y)"
        >
                    
       <img
        v-bind:src="area[x][y].icon"
        v-bind:class="icon"
        >
            
          
        </div>
      </div>
    </main>
    <button v-on:click=start(snake[0].x,snake[0].y,1)>
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