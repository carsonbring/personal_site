
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

  onMount (async() => {
    const response = await fetch('https://site-backend-9ce1fd9af9f0.herokuapp.com/blog')
    posts = await response.json()
    posts.reverse()
    console.log(posts)
  })
</script>
<body class="flex flex-col min-h-screen bg-gradient-to-r from-emerald-950   to-slate-900  " >
  <div class="container mx-auto my-8 p-4">
    {#if posts.length > 0}
      <div class="space-y-4">
        {#each posts as post}
          <div class="bg-pale shadow-lg rounded-lg p-2 opacity-90">
            <div class="bg-slate-950 shadow-lg rounded-lg p-8"> 
              <h3 class="text-2xl font-bold mb-2">{post.title}</h3>
              <h5 class="text-xl font-bold">Date : {post.date} </h5>
              <h5 class="text-xl font-bold">Date : {post.time} </h5>
              <p>{post.content}</p>
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


