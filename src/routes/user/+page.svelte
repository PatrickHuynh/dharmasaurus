<script>
	import supabaseDb from '$lib/supabaseClient';
	import { goto } from '$app/navigation';

	const user = supabaseDb.user;
	if (!user) {
		goto('/user/login');
	}
	const logout = async () => {
		await supabaseDb.signOut();
		goto('/');
	};
</script>

<div class="container h-full mx-auto flex flex-col justify-center items-center space-y-3">
	{#if $user}
		<p>Hello {$user.email}!</p>
		<button type="button" class="btn variant-filled-surface m-0 px-3 py-1 rounded" on:click={logout}
			>Sign out</button
		>
	{:else}
		<a href="/user/login" class="btn variant-filled-surface m-0 px-3 py-1 rounded">Login</a>
	{/if}
</div>
