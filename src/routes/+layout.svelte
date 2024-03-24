<script lang="ts">
	import { page } from '$app/stores';
</script>

<svelte:head>
	<meta charset="UTF-8" />
	<meta http-equiv="X-UA-Compatible" content="IE=edge" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0" />
	<link rel="stylesheet" href="https://unpkg.com/modern-css-reset/dist/reset.min.css" />
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" />
	<link
		href="https://fonts.googleapis.com/css2?family=M+PLUS+1p:wght@100;300;400;500;700;800;900&display=swap"
		rel="stylesheet"
	/>
	<link
		rel="stylesheet"
		href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200"
	/>
	<link
		rel="stylesheet"
		href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200"
	/>
	<link
		rel="stylesheet"
		href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200"
	/>
	<link
		rel="stylesheet"
		href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200"
	/>
	<link
		rel="stylesheet"
		href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200"
	/>
</svelte:head>

<input id="checkbox" type="checkbox" />
<header>
	<div>
		<p>備品管理システム</p>
	</div>
	<nav>
		<ul>
			<li>
				<p>ダッシュボード</p>
				<span class="material-symbols-outlined"> dashboard </span>
			</li>
			<li>
				<p>一覧</p>
				<span class="material-symbols-outlined"> database </span>
			</li>
			<li>
				<p>配置図</p>
				<span class="material-symbols-outlined"> map </span>
			</li>
			<li>
				<p>設定</p>
				<span class="material-symbols-outlined"> settings </span>
			</li>
			<li id="menu">
				<div>
					{#if !$page.data.user}
						<a href="/login">ログイン</a>
						<p>/</p>
						<a href="/register">新規登録</a>
					{:else}
						<form action="/logout?/logout" method="POST">
							<button>ログアウト</button>
						</form>
					{/if}
				</div>
				<label for="checkbox"><span class="material-symbols-outlined"> menu </span></label>
			</li>
		</ul>
	</nav>
</header>
<main>
	<slot />
</main>

<style lang="scss">
	:global(body) {
		font-family: 'M PLUS 1p', sans-serif;
		font-weight: 400;
		font-style: normal;
	}
	header {
		z-index: 999;
		width: 300px;
		height: 100vh;
		background-color: rgb(115, 192, 255);
		position: fixed;

		display: grid;
		grid-template-columns: 1fr;
		grid-template-rows: 80px 1fr;
		gap: 20px;

		nav {
			height: 100%;
		}

		ul {
			width: 100%;
			height: 100%;

			margin: 0;
			padding: 0;

			display: grid;
			grid-template-columns: 1fr;
			grid-template-rows: repeat(4, 100px) 1fr 100px;
			gap: 10px;

			li {
				list-style: none;
				cursor: pointer;

				display: grid;
				grid-template-columns: 1fr 80px;

				p {
					font-size: 1.5em;
					display: flex;
					justify-content: right;
					align-items: center;
				}
				span {
					font-size: 2.5em;
					display: flex;
					justify-content: center;
					align-items: center;
				}
			}

			#menu {
				grid-row: 6 / 7;
				cursor: default;

				div {
					display: flex;
					justify-content: center;
					align-items: center;

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
				}

				label {
					display: flex;
					justify-content: center;
					align-items: center;
				}

				span {
					grid-column: 2 / 3;
					cursor: pointer;
				}
			}
		}
	}

	header {
		transform: translateX(-220px);
		transition: all 300ms 0s ease;
	}

	input[type='checkbox'] {
		display: none;

		&:checked {
			~ header {
				transform: translateX(0px);
			}
		}
	}

	main {
		margin-left: 80px;
	}
</style>
