<script lang="ts">

    let myTask : Array<string> = [];
    let newTask : string = "";


    function addTask(newTask : string){
        if (newTask === ""){
            alert("Veuillez entrer une tâche");
            return;
        };
        
        myTask = [...myTask, newTask];
        newTask = "";
    }

    function removeTask(index : number){
        myTask = myTask.filter((task, i) => i !== index);

    }
    

</script>

<svelte:head>
    <title>Todo</title>
    <meta name="description" content="A todo list" />
</svelte:head>

<div class="text-column">
    <h1>My Todo</h1>
    <ul>
        <slot/>
        {#each myTask as task , index}
            <li> <button type="button" on:click={(e) => removeTask(index)}>{task}</button></li>
        {/each}
    </ul>
</div>

<from>
    <input type="text" bind:value="{newTask}">
    <button type="button" on:click={(e) => addTask(newTask)}>Ajouter</button>
</from>

