<script>

import { initializeApp } from "firebase/app";
import { getFirestore, collection, onSnapshot,doc, updateDoc, deleteDoc, addDoc} from "firebase/firestore";
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



   
    let task="";

        
    const addTodo = async() => {
        if (task !== "" ){
            const docRef = await addDoc(collection(db, "todos"),{
                task:task,
                isComplete:false,
                createdAt:new Date(),
            }) 
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

</script>
<body>
<p class = heading>TODO</p>

<div class = "Texte">
    <input type="text" class = "todotxt" placeholder="Add a Task"  maxlength="200" rows="100" cols="300" bind:value={task} />
    <button class = "addbtn" on:click={addTodo}>+</button>    
</div>
    

<div class = everything>



<link href='https://fonts.googleapis.com/css?family=Poppins' rel='stylesheet'>

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
</div>
</body>


<svelte:window on:keydown={keyIsPressed} />

<style>
    .complete{
        text-decoration: line-through;
    }
    .heading{
        padding-left: 46%;
        font-family: "Poppins",sans-serif;
        font-weight: bold;
        font-size: 250%;
    }
    .everything{
        padding-left: 42%;
        font-family: "Poppins",sans-serif;
        font-size : 26px;
    }
    .todotxt{
        background-color: #f1f99d;
        font-size: 130%;
        font-family: Poppins,sans-serif;
        border: none;
        height: 10%;
        width: 450px;
        padding-left: 2%;
        border-radius: 15px;
        padding-top: 2%;
        padding-right: 2%;
        padding-bottom: 2%;
        text-transform: capitalize;
    }
    .Texte{
        padding-left: 31%;
        padding-bottom: 100px;
        padding-top: 30px;
    }
    ::placeholder { /* Chrome, Firefox, Opera, Safari 10.1+ */
        color: black;
        opacity: 0.5; /* Firefox */
    }
    .addbtn{
        border-radius : 30%;
        padding : 10px;
        
    }
</style>