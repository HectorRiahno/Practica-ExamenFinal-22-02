<script setup>
const props=defineProps({
  friend:{
    type:String,
    default:''
  },
  index:{
    type:Number
  }
  
})

const emit = defineEmits(['borraramigo','agregaramigo'])

function borrarAmigo(index){
  emit('borrarAmigo',index)
}

</script>
<template>
    <div class="flex justify-between">
      <h1 class="text-white">{{ props.friend.nombre }}</h1><h1 class="" @click="borrarAmigo(props.index)">Borrar</h1>
      <h1 v-if="props.friend.estado==true" class="text-green-300 flex"> Conectado 
        <div class="bg-green-300 w-2 h-2 rounded-full"></div>
      </h1>
      <h1 v-else class="text-white flex"> Desconectado 
        <div class="bg-white w-2 h-2 rounded-full"></div>
      </h1>
    </div>
</template>