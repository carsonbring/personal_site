<script>
    import { writable } from 'svelte/store';
    import { Navbar, Footer } from '$lib';
    
    const secretKey = writable('');
    const title = writable('');
    const content = writable('');
    const message = writable('');
    const showMessage = writable(false);
    const currentDate = new Date().toLocaleDateString();
    const currentTime = new Date().toLocaleTimeString();

    async function submitPost() {
      const key = $secretKey;
      const postTitle = $title;
      const postContent = $content;
      const backendUrl = 'https://site-backend-9ce1fd9af9f0.herokuapp.com/blog';
      console.log(currentDate);
      console.log(currentTime); 
      try {
        const response = await fetch(backendUrl, {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
            'secret-key': key, 
          },
          body: JSON.stringify({
            title: postTitle,
            date: currentDate,
            time: currentTime,
            content: postContent,
          }),
        });
        
        if (!response.ok) {
          throw new Error(`Error: ${response.statusText}`);
        }
        
        console.log('Post submitted successfully:');
       
        message.set('Post successful!');
        showMessage.set(true);
         //get rid of success message after 10 seconds
        setTimeout(() => {
            showMessage.set(false);
        }, 10000);

        
      } catch (error) {
        console.error('Error submitting post:', error);
        if (error instanceof Error) {
            message.set(`Error submitting post: ${error.message}`);
        }
        showMessage.set(true);
        setTimeout(() => {
            showMessage.set(false);
        }, 10000);
      }
    }
  </script>
  <Navbar />
  <!-- The Form UI -->

  <body class="flex flex-col min-h-screen bg-gradient-to-r from-emerald-950   to-slate-900">
    <div class="bg-pale shadow-lg rounded-lg p-2 opacity-90 mr-2  align-self-start" style="align-self: flex-start">
      <div class="bg-slate-950 shadow-lg rounded-lg p-8">
  
        <div class="m-4">
          <input
            type="text"
            bind:value={$secretKey}
            placeholder="Secret Key"
            class="w-full p-2 border-2 border-gray-300 rounded-md focus:outline-none focus:border-emerald-500 mb-4"
          />
          <input
            type="text"
            bind:value={$title}
            placeholder="Title"
            class="w-full p-2 border-2 border-gray-300 rounded-md focus:outline-none focus:border-emerald-500 mb-4"
          />
          <textarea
            bind:value={$content}
            placeholder="Content"
            class="w-full h-40 p-2 border-2 border-gray-300 rounded-md focus:outline-none focus:border-emerald-500 mb-4"
          ></textarea>
          <button
            on:click={submitPost}
            class="px-4 py-2 bg-emerald-500 text-white font-semibold rounded-md hover:bg-emerald-600 focus:outline-none focus:ring-2 focus:ring-emerald-300"
          >
            Submit Post
          </button>
        </div>
      </div>
    </div>
  
    <!-- Success Message -->
    {#if $showMessage}
      <p>{$message}</p>
    {/if}

  </body>
  <Footer />
  <style>
  </style>
  