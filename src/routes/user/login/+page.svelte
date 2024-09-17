<script>
	import supabaseDb from '$lib/supabaseClient';

	let email,
		sent = false;

	const user = supabaseDb.user;

	async function submit() {
		sent = true;
		await supabaseDb.signIn(email);
	}

	const signInWithGoogle = async () => {
		await supabaseDb.signInWithOAuth('google');
	};

	function focus(element) {
		element.focus();
	}

	const logout = async () => {
		await supabaseDb.signOut();
		goto('/');
	};
</script>

<div class="container h-full mx-auto flex justify-center items-center">
	{#if $user}
		<button
			class="flex space-x-2 justify-center items-center rounded-md bg-surface-400 px-3 py-2 text-sm font-medium text-white"
			on:click={logout}>Sign out {$user?.email}</button
		>
	{:else if sent}
		<p class="py-5 font-medium">Email sent!</p>
	{:else}
		<div class="flex flex-col space-y-3">
			<!-- <form class="flex flex-col space-y-3" on:submit|preventDefault={submit}>
				<label class="label">
					<span>E-mail Address</span>
					<input class="input" name="email" type="email" required bind:value={email} use:focus />
				</label>
				<button
					class="flex space-x-2 justify-center items-center rounded-md bg-surface-400 px-3 py-2 text-sm font-medium text-white"
				>
					<svg
						class="icon"
						height="24"
						xmlns="http://www.w3.org/2000/svg"
						fill="none"
						viewBox="0 0 24 24"
						stroke="currentColor"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"
						/>
					</svg>
					<span>Send me a magic link</span>
				</button>
			</form> -->
			<button
				class="flex space-x-2 justify-center items-center rounded-md bg-surface-400 px-3 py-2 text-sm font-medium text-white"
				on:click={signInWithGoogle}>Sign in with Google</button
			>
		</div>
	{/if}
</div>
