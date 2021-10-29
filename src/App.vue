<script setup>
import {ref} from "vue";
const todos = ref ([
    {id:0, content:"hello", done: false},
    {id:1, content: "world", done:false},
    {id:2, content: "Hi", done:true},

]);

const pending = computed(()=> {
    return todos.value.filter((todo) => !todo.done);
});

const completed = computed(()=> {
    return todos.value.filter((todo) => todo.done);
});

</script>

<template>
<div class= "min-h-screen bg-gray-800">
    <div class= "container flex flex-col pt-8 mx-auto space-y-8">
 <h1 class ="font-thin tracking-tight text-center text 6xl">My ToDo App</h1>
 <input type="text" class= "px-4 py-2 text-xl text-center rounded-lg" placeholder="New ToDo">
 <div class="flex justify-around ">
     <div class= "w-1/3"></div>
     <h3 class= "text-2xl text-center text-blue-400 ">Pending</h3>
     <ul class= "pt-8 space-y-4">
         <li 
         v-for="todo in pending" 
         :key="todo.id"
          class= "w-full px-4 py-2 font-bold text-center text-blue-600 bg-gray-300 rounded-lg hover:cursor-pointer hover:bg-blue-400 hover:text-gray-200 duration 500">
            {{ todo.content }}
         </li>
        
         </ul>    
 </div>
 <div class="w-1/3">
     <h3 class= "text-2xl text-center text-green-400">Completed</h3>
     <ul>
         <li v-for="todo in completed" 
         :key="todo.id"
         class= "w-full px-4 py-2 font-bold text-center text-green-600 bg-gray-300 rounded-lg hover:cursor-pointer hover:bg-green-400 hover:text-gray-200 duration 500">Three
         {{ todo.content }}
         </li>
     </ul>
 </div>
 </div>
 </div>
</template>

