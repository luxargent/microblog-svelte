<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    let text = '';

    const handleSubmit = () => {
        if (text.trim() === '') return;

        dispatch('addPost', text);
        text = '';
    }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="What's on your mind?" bind:value={text} />
    <button type="submit">Post</button>
</form>

<style>
    form {
        display: flex;
        gap: 0.5rem;
        margin-bottom: 1rem;
    }
    input {
        flex: 1;
        padding: 0.5rem;
    }
    button {
        padding: 0.5rem 1rem;
    }
</style>