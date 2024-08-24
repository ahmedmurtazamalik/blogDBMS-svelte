<script>
    export let blog;
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    const handleIncrement = (title,field) => {
        dispatch('increment',{title,field});
    }


    const handleDecrement = (title,field) => {
        dispatch('decrement',{title,field});
    }

    const handleDelete = (title) => {
        dispatch('delete',title);
    }

</script>


<div class="blog">
    <div class="field">
      <label for="title">Title:</label>
      <span id="title">{blog.title}</span>
    </div>
  
    <div class="field">
      <label for="views">Views:</label>
      <span id="views">{blog.views}</span>
      <button class="btn-adjust" on:click={() => handleIncrement(blog.title,'1')}>+</button>
      <button class="btn-adjust" on:click={() => handleDecrement(blog.title,'1')}>-</button>
    </div>
  
    <div class="field">
      <label for="likes">Likes:</label>
      <p id="likes">{blog.likes}</p>
      <button class="btn-adjust" on:click={() => handleIncrement(blog.title,'2')}>+</button>
      <button class="btn-adjust" on:click={() => handleDecrement(blog.title,'2')}>-</button>
    </div>
  
    <div class="field">
      <label for="comments">Comments:</label>
      <span id="comments">{blog.comments}</span>
      <button class="btn-adjust" on:click={() => handleIncrement(blog.title,'3')}>+</button>
      <button class="btn-adjust" on:click={() => handleDecrement(blog.title,'3')}>-</button>
    </div>

    <div class="field">
        <label for="shares">Shares:</label>
        <span id="shares">{blog.shares}</span>
        <button class="btn-adjust" on:click={() => handleIncrement(blog.title,'4')}>+</button>
        <button class="btn-adjust" on:click={() => handleDecrement(blog.title,'4')}>-</button>
    </div>
  
    <div class="field">
        <label for="ads">Ads:</label>
        <span id="ads">{blog.ads}</span>
        <button class="btn-adjust" on:click={() => handleIncrement(blog.title,'5')}>+</button>
        <button class="btn-adjust" on:click={() => handleDecrement(blog.title,'5')}>-</button>
    </div>

    <button class="btn-delete" on:click={() => handleDelete(blog.title)}>Delete</button>
</div>


<style>
    .blog {
        max-width: 500px;
        margin: 0 auto;
        margin-bottom: 30px;
        padding: 20px;
        border: 1px solid #ccc;
        border-radius: 8px;
        background-color: #f9f9f9;
    }

    .field {
        margin-bottom: 15px;
        display: flex;
        align-items: center;
    }

    .field label {
        font-weight: bold;
        font-size: 1.05em;
        margin-right: 10px;
        width: 100px; 
    }

    .field span, .field p {
        flex-grow: 1;
        padding: 10px;
        border: 1px solid #ccc;
        border-radius: 4px;
        font-size: 1em;
        background-color: #fff;
        text-align: center;
        width: 150px; 
    }

    .btn-adjust {
        font-weight: bolder;
        margin-left: 10px;
        margin-top: 5px;
        padding: 5px 10px;
        border: 1px solid #ccc;
        border-radius: 4px;
        background-color: #e0e0e0;
        cursor: pointer;
        font-size: 1em;
        transition: background-color 0.3s ease;
    }

    .btn-adjust:hover {
        background-color: #ccc;
    }

    .btn-delete {
        margin-left: 40.2%;
        font-weight: bold;
        margin-top: 20px;
        padding: 10px 20px;
        border: 1px solid #ff4d4d;
        border-radius: 4px;
        background-color: #ff4d4d;
        color: #fff;
        cursor: pointer;
        font-size: 1em;
        transition: background-color 0.3s ease;
    }

    .btn-delete:hover {
        background-color: #e03e3e;
    }
</style>