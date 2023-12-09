<script setup>
import { ref } from 'vue';
import FriendsComponents from '@/components/FriendsComponents.vue';
let cont=1
let newFriend=ref('')
const array=ref([{nombre:'Hygge',estado:true},
{nombre:'SoyQuill0',estado:true},
{nombre:'Thoshu',estado:false}])

function addFriend(){
  if(newFriend.value.trim()===''){return}
  
  if(cont%2==0){
    const actu={nombre:newFriend.value,estado:true}
     array.value.push(actu)
  }else{
    const actu={nombre:newFriend.value,estado:false}
    array.value.push(actu)
  }
  cont++
  newFriend.value=''
}

function deleteAmigo(i){
  array.value.splice(i,1)
}


</script>

<template>
  
  <div class=" bg-black/80 w-72 h-96 mx-auto mt-10 rounded-md">
    <div class="bg-gradient-to-b from-cyan-500 to-cyan-950 rounded-md">
      <div class="flex"><p class=" font-bold uppercase mx-auto mt-2">perfil</p></div>
      <div class="flex p-3"><img class="w-10" src="https://fcb-abj-pre.s3.amazonaws.com/img/jugadors/763_ronaldinho.jpg" alt="">
        <p class="ml-3">Hjrianol10</p>
      </div>
    </div>
    <div class="bg-gray-500 flex justify-between items-center px-2 py-1">
      <p class="uppercase font-normal text-white">amigos</p>
      <input v-model="newFriend"  class="rounded bg-neutral-800 text-white  hover:bg-neutral-600" type="text">
      <p @click="addFriend" class="flex font-extrabold text-xl  text-stone-800 hover:text-white hover:cursor-pointer ">+</p>
    </div>

    <FriendsComponents v-for="(obj,i) in array" :key="i" :friend="obj" :index="i" @borrarAmigo="deleteAmigo"></FriendsComponents>
  </div>
</template>

<style scoped>

</style>
