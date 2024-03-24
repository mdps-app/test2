<script lang="ts">
	import { goto } from '$app/navigation';
	import type { PageData } from './$types';
	import Thread from '$lib/Thread.svelte';
	export let data: PageData;
</script>

<svelte:head>
	<meta charset="UTF-8" />
	<meta http-equiv="X-UA-Compatible" content="IE=edge" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0" />
	<link rel="stylesheet" href="https://unpkg.com/modern-css-reset/dist/reset.min.css" />
	<title>Document</title>
</svelte:head>

<main>
	<h1>スレッド一覧</h1>
	<button type="button" on:click={() => goto('/post')}>投稿する</button>
	{#each data.threads as thread}
		<Thread id={thread.id} content={thread.content} />
	{/each}
</main>

<style lang="scss">
    
</style>