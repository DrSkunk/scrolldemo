<script>
	import { onMount } from 'svelte';

	const filler = new Array(1000);

	const speeds = [-1000, -100, -50, -25, -10, -5, -1, 0, 1, 5, 10, 25, 50, 100, 1000];
	let speed = 0;

	let behavior = 'smooth';

	const toggleBehavior = () => {
		behavior = behavior === 'smooth' ? 'auto' : 'smooth';
	};

	const setSpeed = (newSpeed) => {
		speed = newSpeed;
	};

	onMount(() => {
		setInterval(() => {
			window.scrollBy({
				top: speed,
				behavior: behavior
			});
		}, 10);
	});
</script>

<div class="sticky top-0">
	<button class="border px-4 py-2 bg-indigo-100 mb-3" on:click={() => toggleBehavior()}
		>Toggle behavior: now {behavior}</button
	>
	<div class="flex gap-2 flex-wrap">
		{#each speeds as speed}
			<button class="border px-4 py-2 bg-indigo-100" on:click={() => setSpeed(speed)}
				>Speed {speed}</button
			>
		{/each}
	</div>
</div>
<h1 class="text-3xl font-bold underline">Scrolling</h1>

{#each filler as _, i}
	<div class="text-6xl">
		Hello world!
		{i}
	</div>
{/each}
