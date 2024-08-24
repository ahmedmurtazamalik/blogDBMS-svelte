<script>
	import Header from './Header.svelte'
	import Footer from './Footer.svelte'
	import Tabs from './Tabs.svelte'
	import AddBlog from './AddBlog.svelte';
  	import BlogList from './BlogList.svelte';

	let tabs = ['All Blogs','Add New Blog'];
	let activetab = 'All Blogs';

	let blogs = [
		{title: 'Dummy', views: '5', likes: '4', comments: '3', shares: '2', ads: '1'},
	];

	const tabChanger = (e) => {
		activetab = e.detail;
	}

	const addBlogHandler = (e) => {
		const blog = { ...e.detail }; 
		blogs = [blog, ...blogs];
		console.log(blogs);
		activetab = 'All Blogs';
	}

	const handleIncrement = (e) => {
		const {title,field} = e.detail;
		let copiedBlogs = [...blogs];
		let blog = copiedBlogs.find(blog => blog.title === title);

		if(field == 1){ blog.views++; }
		else if (field == 2) { blog.likes++; }
		else if (field == 3) { blog.comments++; }
		else if (field == 4) { blog.shares++; }
		else if (field == 5) { blog.ads++; }

		blogs = copiedBlogs;
	}

	const handleDecrement = (e) => {
		const {title,field} = e.detail;
		let copiedBlogs = [...blogs];
		let blog = copiedBlogs.find(blog => blog.title === title);

		if(field == 1 && blog.views > 0){ blog.views--; }
		else if (field == 2 && blog.likes > 0) { blog.likes--; }
		else if (field == 3 && blog.comments > 0) { blog.comments--; }
		else if (field == 4 && blog.shares > 0) { blog.shares--; }
		else if (field == 5 && blog.ads > 0) { blog.ads--; }

		blogs = copiedBlogs;
	}

	const handleDelete = (e) => {
		const title = e.detail;
		let copiedBlogs = [...blogs];
		copiedBlogs = copiedBlogs.filter(blog => blog.title != title);
		blogs = copiedBlogs;
	}

</script>

<main>
	<Header/>

	<Tabs {tabs} {activetab} on:tabChange={tabChanger}/>
	{#if activetab === 'All Blogs'}
		<BlogList {blogs} on:increment={handleIncrement} on:decrement={handleDecrement} on:delete={handleDelete}/>
	{:else if activetab === 'Add New Blog'}
		<AddBlog on:AddNewBlog={addBlogHandler}/>
	{/if}
	
	<Footer/>
</main>

<style>


</style>