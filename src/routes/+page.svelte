<script>

import { initializeApp } from "firebase/app";
import { getFirestore, collection, onSnapshot} from "firebase/firestore";
import {firebaseConfig} from "$lib/firebaseConfig";

const firebaseApp = initializeApp(firebaseConfig);

const db =  getFirestore();

const colRef = collection(db, "todos");

let todos = [ ];

const unsubscribe = onSnapshot(colRef, (querySnapshot) => {
    let fbTodos = [];
  querySnapshot.forEach((doc) => {
    let todo = {...doc.data(),id : doc.id}
    fbTodos = [todo,...fbTodos];
  });
  console.table(fbTodos);
});


console.log({firebaseApp,db});

   
    let task="";

        
    const addTodo = () => {
        let todo = {
            task:task,
            isComplete:false,
            createdAt:new Date(),
        };
        if (task !== "" ){
            todos = [todo,...todos]; 
        }
        
        task = "";
    }
    const markTodoAsComplete = (index) => {
        todos[index].isComplete = !todos[index].isComplete;
    }
    const deleteTodo = (index) => {
        let deleteItem = todos[index];
        console.log(deleteItem);
        todos = todos.filter((item) => item !=deleteItem);
    }
    const keyIsPressed = (event) =>{
        if(event.key === "Enter"){
            addTodo();
        }
    }

        $: console.table(todos);
</script>

<input type="text" placeholder="Add a Task" bind:value={task} />
<button on:click={addTodo}>Add</button>

<ol>
    {#each todos as item,index}
    <li class:complete={item.isComplete}>
    <span>
        {item.task}
    </span>
    <span>
        <button on:click={() => markTodoAsComplete(index)}>✔</button>
        <button on:click={() => deleteTodo(index)}>✖</button>
    </span>
    </li>
    {:else}
    <p>No Todos Found</p> 
    {/each}
</ol>

<svelte:window on:keydown={keyIsPressed} />

<style>
    .complete{
        text-decoration: line-through;
    }
</style>