<script>
	import '../app.postcss';

	// Highlight JS
	import hljs from 'highlight.js/lib/core';
	import 'highlight.js/styles/github-dark.css';
	import { storeHighlightJs } from '@skeletonlabs/skeleton';
	import xml from 'highlight.js/lib/languages/xml'; // for HTML
	import css from 'highlight.js/lib/languages/css';
	import javascript from 'highlight.js/lib/languages/javascript';
	import typescript from 'highlight.js/lib/languages/typescript';

	hljs.registerLanguage('xml', xml); // for HTML
	hljs.registerLanguage('css', css);
	hljs.registerLanguage('javascript', javascript);
	hljs.registerLanguage('typescript', typescript);
	storeHighlightJs.set(hljs);

	// Floating UI for Popups
	import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';
	import { storePopup } from '@skeletonlabs/skeleton';
	storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });

	// backend
	import supabaseDb from '../lib/supabaseClient';
	import Navigation from '../lib/navigation/navigation.svelte';
	const user = supabaseDb.user;
	const logout = async () => {
		await supabaseDb.signOut();
		goto('/');
	};
</script>

<Navigation />

<!-- 
<nav class="bg-gray-800">
	<div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
		<div class="relative flex h-16 items-center justify-between content-center">
			<div class="flex flex-1 items-center justify-center sm:items-stretch sm:justify-start">
				<div class="flex flex-shrink-0 items-center"></div>
				<div class="hidden sm:ml-6 sm:block">
					<div class="flex space-x-4 content-center">
						<button class="btn btn-sm mr-4" on:click={sideBarOpen}>
							<span>
								<svg viewBox="0 0 100 80" class="fill-token w-4 h-4">
									<rect width="100" height="20" />
									<rect y="30" width="100" height="20" />
									<rect y="60" width="100" height="20" />
								</svg>
							</span>
						</button>
						<img src={dharmasaurusLogo} alt="Dharmasaurus" class="h-8" />
						<span class="font-bold p-0 m-0">Dharmasaurus</span>
						<a
							href="/"
							class="rounded-md bg-gray-900 px-3 py-2 text-sm font-medium text-white"
							aria-current="page">Definitions</a
						>
					</div>
				</div>
			</div>
			<div
				class="absolute inset-y-0 right-0 flex items-center pr-2 sm:static sm:inset-auto sm:ml-6 sm:pr-0"
			></div>
			{#if $user}
				<button
					class="rounded-md bg-gray-900 px-3 py-2 text-sm font-medium text-white"
					on:click={logout}>Sign out</button
				>
			{:else}
				<a href="/login" class="rounded-md bg-gray-900 px-3 py-2 text-sm font-medium text-white"
					>Login</a
				>
			{/if}
		</div>
	</div>
</nav> -->
<slot />
