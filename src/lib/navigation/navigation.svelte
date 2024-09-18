<script>
	// menu modal
	import { getDrawerStore, initializeStores, Drawer } from '@skeletonlabs/skeleton';
	import sideBarMenu from '$lib/navigation/sideBarMenu.svelte';

	const drawerSettings = {
		id: 'main-menu',
		bgBackdrop: 'bg-gradient-to-tr from-indigo-500/50 via-purple-500/50 to-pink-500/50',
		width: 'w-full sm:w-96',
		padding: 'p-4',
		rounded: 'rounded-xl'
	};

	initializeStores();
	const sideBarMenuDrawer = getDrawerStore();

	const sideBarOpen = () => {
		sideBarMenuDrawer.open(drawerSettings);
	};

	import dharmasaurusLogo from '$lib/imgs/dharmasaurus_small.png';

	// backend
	import supabaseDb from '$lib/supabaseClient';
	import SideBarMenu from './sideBarMenu.svelte';
	const user = supabaseDb.user;
</script>

<Drawer>
	<SideBarMenu />
</Drawer>

<nav class="bg-surface-700 mb-3">
	<div class="container mx-auto flex justify-between items-center px-5 py-3 max-w-7xl">
		<div class="flex items-center">
			<button on:click={sideBarOpen}>
				<svg viewBox="0 0 100 100" class="fill-surface-100 w-8 h-6">
					<rect y="20" width="100" height="10" />
					<rect y="45" width="100" height="10" />
					<rect y="70" width="100" height="10" />
				</svg>
			</button>
		</div>
		<a href="/" class="flex space-x-2 items-center">
			<img src={dharmasaurusLogo} alt="Dharmasaurus" class="flex-none h-8" />
			<span class="font-bold">Dharmasaurus</span>
		</a>
		<div>
			{#if $user}
				<a href="/user" class="btn variant-filled-surface m-0 px-3 py-1 rounded">Profile</a>
			{:else}
				<a href="/user/login" class="btn variant-filled-surface m-0 px-3 py-1 rounded">Login</a>
			{/if}
		</div>
	</div>
</nav>
