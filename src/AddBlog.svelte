<script>
    import Button from './Button.svelte'
    import { createEventDispatcher } from 'svelte';

    let answers = {title: '', views: '', likes: '', comments: '', shares: '', ads: ''};
    let error = "";

    let dispatch = createEventDispatcher();

    function validationCheck(){
        if(answers.title.trim().length >= 10){
            if(answers.views !== '' && answers.views >= 0 && answers.likes !== '' && answers.likes >= 0 && answers.comments !== '' && answers.comments >= 0 && answers.shares !== '' && answers.shares >= 0 && answers.ads !== '' && answers.ads >= 0){ return true }
        }
        return false
    }

    const submitHandler = () => {
        let valid = validationCheck();
        if(!valid) {error = "Title must be atleast 10 characters long and numerical values must be non-negative."}
        else{
            dispatch('AddNewBlog',answers);
        }
    }

</script>


<form class="blog-form" on:submit|preventDefault={submitHandler}>
    <div class="field">
        <label for="title" class="blog-title">Add New Blog</label>
    </div>

    <div class="field">
        <label for="blogtitle" class="question-label">Blog Title</label>
        <input type="text" id="blogtitle" class="form-input" bind:value={answers.title}>
    </div>

    <div class="field">
        <label for="views" class="question-label">Views</label>
        <input type="number" id="views" class="form-input" bind:value={answers.views}>
    </div>

    <div class="field">
        <label for="likes" class="question-label">Likes</label>
        <input type="number" id="likes" class="form-input" bind:value={answers.likes}>
    </div>


    <div class="field">
        <label for="comments" class="question-label">Comments</label>
        <input type="number" id="comments" class="form-input" bind:value={answers.comments}>
    </div>

    <div class="field">
        <label for="shares" class="question-label">Shares</label>
        <input type="number" id="shares" class="form-input" bind:value={answers.shares}>
    </div>


    <div class="field">
        <label for="ads" class="question-label">Ads</label>
        <input type="number" id="ads" class="form-input" bind:value={answers.ads}>
    </div>

    <Button/>

    <div class="error">{error}</div>

</form>

<style>
    .blog-form {
    max-width: 500px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 8px;
    background-color: #f9f9f9;
    }

    .field {
        margin-bottom: 15px;
    }

    .blog-title {
        text-align: center;
        display: block;
        font-weight: bold;
        font-size: 1.2em;
        margin-bottom: 10px;
    }

    .question-label {
        display: block;
        font-weight: bold;
        margin-bottom: 5px;
    }

    .form-input {
        width: 100%;
        padding: 10px;
        border: 1px solid #ccc;
        border-radius: 4px;
        font-size: 1em;
        text-align: center;
    }

    .error{
        text-align: center;
        color: red;
    }
</style>