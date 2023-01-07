<script setup>
  import{ref} from 'vue'

  

  const f = {name:"food",color:"red",icon:"./src/assets/apple.png"}
  const h ={name:"head",color:"blue",icon:"./src/assets/head_down.png"}
  const b = {name:"body",color:"blue",icon:"./src/assets/body_horizontal.png"}
  const t ={name:"tail",color:"blue",icon:"./src/assets/tail_down.png"}  
  
  let area = ref([
  
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],
  ['','','','','','','','','',''],

])

let snake = [ {x: 4, y: 3} , {x: 4, y: 4} , {x: 4, y:5}]
let fps = 1000/15;
let gameloop;

// let randFood = () =>{

//   let x = Math.floor(Math.random()*8)
//   let y = Math.floor(Math.random()*8)

//   area.value[x][y]=f

// }


  const tiles = (x,y)=>{
  if((x+y)%2==0){
      return 'white';
    }
    else{
      return 'black';
    }
  }


  // let frame = () => {
  //  drawBoard()
  //  drawFood()
  //  moveSnake()
  //  drawSnake()
   
  //  if(hitWall()||hitSelf()){
  //   clearInterval(gameloop)
  //   gameOver();
  //  }

  // }
  // gameloop = setInterval(frame(),fps)

  let drawSnake = (snake) =>{
    snake.forEach((tile)=>{
      drawSprite(tile.x,tile.y)
    })
  }

  let drawSprite = (x,y) => {
    area.value[x][y] = b
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
    <button v-on:click=drawSnake(snake)>
      drawSnake
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