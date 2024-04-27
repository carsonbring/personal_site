<script context="module" lang="ts">
  import { Navbar, Footer } from '$lib';
  
  interface BlogPost {
    title: string;
    content: string;
    date : string;
    time : string;

  }

</script>
<Navbar />
<script lang="ts">
  import {onMount} from 'svelte'
  let posts: BlogPost[] = [];
  let blog_start = 0;
  onMount (async() => {
    const response = await fetch(`${import.meta.env.VITE_BACKEND_URL}/blog`)
    posts = await response.json()
    posts.reverse()
    console.log(posts)
  })
</script>
<body class="flex flex-col min-h-screen bg-gradient-to-r from-emerald-950   to-slate-900  " >
  <br>
  <div class="flex space-x-4 justify-end p3 mr-10 font-bold">
    <button
        class="bg-slate-950 text-orange-100   hover:bg-emerald-950 hover:text-white p-4 rounded-lg shadow-lg"
        on:click={() => {
        blog_start = Math.max(blog_start - 3, 0);
        }}>Previous</button>
    <button
      class="bg-slate-950 text-orange-100   hover:bg-emerald-950 hover:text-white p-4 rounded-lg shadow-lg"
      on:click={() => {
        blog_start = Math.min(blog_start + 3, posts.length - 1);
      }}>Next</button>
      
  </div>
    
  <div class="container mx-auto my-8 p-4">
    {#if posts.length > 0}
      <div class="space-y-4">
        {#each posts.slice(blog_start, blog_start+3) as post}
          <div class="bg-pale shadow-lg rounded-lg p-2 opacity-90">
            <div class="bg-slate-950 shadow-lg rounded-lg p-8"> 
              <h3 class="text-2xl font-bold mb-2">{post.title}</h3>
              <h5 class="text-xl font-bold">Date : {post.date} </h5>
              <h5 class="text-xl font-bold">Date : {post.time} </h5>
              <br>
              <p class="post-content">{post.content}</p>
            </div>
          </div>
        {/each}
      </div>
    {:else}
      <div class="text-center">
        <p class="text-xl">Loading...</p>
      </div>
    {/if}
  </div>
</body>
<Footer />


