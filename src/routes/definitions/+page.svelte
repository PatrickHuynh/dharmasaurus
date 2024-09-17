<script>
	let searchText = '';
</script>

<div class="container h-full mx-auto flex flex-col justify-center items-center">
	<label class="pb-3 w-[80vw] max-w-screen-md">
		<input type="text" placeholder="Search definitions" class="input" bind:value={searchText} />
	</label>
	<span>{searchText}</span>
</div>
