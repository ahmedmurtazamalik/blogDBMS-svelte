<script>
	import BlogDetail from "./BlogDetail.svelte";
	import {fade, slide, scale} from 'svelte/transition';
	import { flip } from 'svelte/animate';
	export let blogs = [];


</script>

<div class="bloglist">
	{#each blogs as blog (blog.title)}
		<div in:fade out:scale|local animate:flip={{duration:500}}>
			<BlogDetail {blog} on:increment on:decrement on:delete/>
		</div>
	{/each}
</div>

<style>
	.bloglist{
		display: grid;
		grid-template-columns: 1fr 1fr;
		grid-gap: 10px;
	}
</style>