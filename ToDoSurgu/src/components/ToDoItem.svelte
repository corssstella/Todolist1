<script>
    export let id;
    export let text;
    export let isDone;
    import{createEventDispatcher} from 'svelte';

    const dispatch=createEventDispatcher();
</script>

<div class="todo-item" class:todo-item_done={isDone}>
    <input 
    class="todo-item_check" 
    type="checkbox" 
    on:change={dispatch('change',{id})} 
    checked={isDone}
    />
    <span class="todo-item_text">{text}</span>
    <button class="todo-item_btn" 
    on:click={dispatch('remove',{id})}>Del</button>
</div>

<style>
    .todo-item{
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 15px;
        background: rgb(250, 195, 195);
        border-radius: 10px;
    }
    .todo-item_done{
        background: rgb(166, 229, 166);
    }
    .todo-item_done .todo-item_text{
        text-decoration: line-through;
    }
    .todo-item_check{
		width: 20px;
		height: 20px;
	}


    .todo-item_text{
        flex-grow: 1;
    }
    .todo-item_btn{
        border: none;
        background-color: rgb(137, 185, 247);
        border-radius: 10px;
        padding: 10px;
        min-width: 100px;
    }
</style>