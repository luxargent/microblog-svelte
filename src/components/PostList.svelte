<script>
    import PostItem from "./PostItem.svelte";
    export let posts = [];
    export let onDelete;
</script>

<div>
    {#each posts as post}
        <PostItem text={post.text} date={post.date} id={post.id} onDelete={onDelete}/>
    {/each}
</div>