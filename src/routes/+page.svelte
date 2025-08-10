<script lang="ts">
    import { format } from 'date-fns';
	import Calendar from '../components/calendar/calendar.svelte';

    const defaultBirthday = format(new Date(), 'yyyy-MM-dd');
    let inputBirthday = $state(defaultBirthday);
    let birthday = $derived(new Date(inputBirthday));
</script>

Här kan jag bestämma vilken dag som är just min födelsedag.
<input type="date" bind:value={inputBirthday} />

<div class="h-screen w-screen flex flex-col items-center justify-center">
	<Calendar birthday={birthday} />
</div>
