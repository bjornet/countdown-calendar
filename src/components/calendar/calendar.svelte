<script lang="ts">
	import { differenceInCalendarDays } from 'date-fns';

	let { birthday } = $props();

	const daysLeft = $derived(differenceInCalendarDays(birthday, new Date()));
	const day = $derived(birthday.getDate());

	const month = $derived(new Intl.DateTimeFormat('sv-SE', { month: 'long' }).format(birthday));
</script>

<div class="max-w-1.5xl mx-auto flex flex-col items-center justify-center gap-4 bg-stone-100 p-8">
	<h1 class="text-2xl">
		Nedräkning till min födelsedag den <strong>{day} {month} {birthday.getFullYear()}</strong>
	</h1>

	<div class="flex flex-col items-center justify-center">
		<img src="https://fillmurray.lucidinternets.com/g/400/200" alt="Djur" />
	</div>

	<p class="text-lg">
		{#if daysLeft > 0}
			Det är <strong>{daysLeft}</strong> dagar kvar till min födelsedag
		{:else if daysLeft === 0}
			Det är min födelsedag idag!
		{:else}
			Den dagen har passerat. ℹ️ Välj ett datum i framtiden.
		{/if}
	</p>
</div>
