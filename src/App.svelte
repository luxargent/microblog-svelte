<script>
  import NewPostForm from "./components/NewPostForm.svelte";
  import PostList from "./components/PostList.svelte";
  import { onMount } from "svelte";

  let posts = [];

  onMount(() => {
    const stored = localStorage.getItem('posts');
    if (stored) {
      posts = JSON.parse(stored);
    }
  })

  const addPost = (text) => {
    const newPost = {
      id: Date.now(),
      text,
      date: new Date().toLocaleString()
    };
    posts = [newPost, ...posts];
    localStorage.setItem('posts', JSON.stringify(posts));
  }

  const deletePost = (id) => {
    posts = posts.filter(post => post.id !== id);
    localStorage.setItem('posts', JSON.stringify(posts)); 
  }
</script>

<main>
  <h1>Microblog Beta</h1>
  <NewPostForm on:addPost={(e) => addPost(e.detail)} />
  <PostList {posts} onDelete={deletePost} />
</main>

<style>
  main {
    padding: 2rem;
    max-width: 600px;
    margin: 0 auto;
  }
  h1 {
    text-align: center;
    margin-bottom: 2rem;
  }
</style>