<script>
    import { Trash } from "lucide-svelte";
    
    export let id;
    export let text;
    export let date;
    export let onDelete;

    const deleteItem = () => {

    }
</script>

<div class="post-card">
    <div>
        <p>{text}</p>
        <small>{date}</small>
    </div>
    <button on:click={() => onDelete(id)}>
        <Trash />
    </button>
</div>

<style>
    .post-card {
        display: flex;
        padding: 1rem;
        margin-bottom: 0.5rem;
        background: #f0f0f0;
        border-radius: 8px;
        text-align: left;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
    }
    p {
        margin: 0 0 0 0.5rem 0;
    }
</style>