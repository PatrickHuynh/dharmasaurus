<script>
	import { getDrawerStore } from '@skeletonlabs/skeleton';
	import dharmasaurusLogo from '$lib/imgs/dharmasaurus_small.png';
	const sideBarMenuDrawer = getDrawerStore();
	const sideBarMenuClose = () => {
		sideBarMenuDrawer.close();
	};
</script>

<div class="flex flex-col h-full justify-between px-6 py-5">
	<div class="flex flex-col justify-start space-y-3">
		<div class="flex flex-row justify-between">
			<a href="/" class="flex space-x-2 items-center" on:click={sideBarMenuClose}>
				<img src={dharmasaurusLogo} alt="Dharmasaurus" class="flex-none h-8" />
				<span class="font-bold">Dharmasaurus</span>
			</a>
			<button on:click={sideBarMenuClose}>
				<svg height="15" width="15" viewBox="0 0 25 25" class="fill-surface-100">
					<line x1="0" y1="0" x2="25" y2="25" style="stroke:darkgrey;stroke-width:3" />
					<line x1="0" y1="25" x2="25" y2="0" style="stroke:darkgrey;stroke-width:3" />
				</svg>
			</button>
		</div>
		<hr class="fill-surface-100" />
		<div>
			<button on:click={sideBarMenuClose}> <a href="/definitions">Definitions</a></button>
		</div>
	</div>
	<div class="mx-auto">Thanks!</div>
	<!-- <nav class="flex flex-col justify-start">
		<h3 class="h3 text-xl uppercase"><a href="/" on:click={drawerClose}>Hodja's D Tools</a></h3>
		<div class="p-2"></div>
		<h4 class="h4">Season 5</h4>
		<hr />
		<ul class="indent-6">
			<li>
				<a href="/season5/masterworkingmats" on:click={drawerClose}>
					Masterworking Materials Calculator
				</a>
			</li>
		</ul>
	</nav>
	<a class="mx-auto w-full" target="_blank" href="https://donate.stripe.com/dR6g0mbOt3Hi7eM3cd">
		<button
			class="btn w-full btn-sm rounded flex flex-row gap-3 border-gray-500 content-center hover:bg-gradient-to-tl hover:from-stone-900 hover:to-orange-600"
			on:click={drawerClose}
		>
			Donate Coffee :)
		</button></a
	> -->
</div>
