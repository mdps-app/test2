<script lang="ts">
	import { page } from '$app/stores';
</script>

{#if !$page.data.user}
	<a href="/login">ログイン</a>
	<p>/</p>
	<a href="/register">新規登録</a>
{:else}
	<form action="/logout?/logout" method="POST">
		<button>ログアウト</button>
	</form>
{/if}

<style lang="scss">
	a {
		float: left;
		cursor: pointer;

		font-size: 1.1em;
		color: rgb(22, 100, 201);
		text-decoration: none;

		transition: color 0.3s;

		&:hover {
			color: rgb(247, 251, 255);
		}
	}
	p {
		float: left;
		margin-left: 10px;
		margin-right: 10px;

		color: rgb(22, 100, 201);
	}
</style>
