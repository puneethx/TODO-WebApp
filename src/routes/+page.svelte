<script>

import { initializeApp } from "firebase/app";
import { getFirestore, collection, onSnapshot,doc, updateDoc, deleteDoc} from "firebase/firestore";
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
  todos = fbTodos;
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
    const markTodoAsComplete = async (item) => {
        await updateDoc(doc(db, "todos", item.id), {
            isComplete: !item.isComplete
        });
    }
    const deleteTodo = async(id) => {
        await deleteDoc(doc(db, "todos", id));
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
    {#each todos as item}
    <li class:complete={item.isComplete}>
    <span>
        {item.task}
    </span>
    <span>
        <button on:click={() => markTodoAsComplete(item)}>✔</button>
        <button on:click={() => deleteTodo(item.id)}>✖</button>
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