<script>
	import { page } from '$app/stores';
</script>

<div class="flex flex-col justify-center mx-auto items-center space-y-3 pt-3">
	<h1 class="h2">Error</h1>
	<p class="max-w-full"><b>Error status code</b>: {$page.status}</p>
	<p class="max-w-full"><b>Description</b>: {$page.error.message}</p>
</div>
