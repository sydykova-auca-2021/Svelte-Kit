<script>
	import FaLinkedin from 'svelte-icons/fa/FaLinkedin.svelte';
	import FaGithub from 'svelte-icons/fa/FaGithub.svelte';
	import FaEnvelope from 'svelte-icons/fa/FaEnvelope.svelte';
	import { modalOpened } from '$lib/store';
	import { Deta } from 'deta';
	const deta = Deta('d0up2qbpfbe_SMDhtCNguTkLnwch6ZWLWpW1dVFbuEA6'); // project_key
	const db = deta.Base('db1');

	let result = '';

	function save() {
		let value = {
			key: '1',
			name: 'Alice',
			age: 20
		};
		db.put(value);
	}

	async function load() {
		let object = await db.get('uwfjlx4e8rou');
		let result = object?.name ?? null;
		console.log(JSON.stringify(result));
	}
</script>

<br />
some changes

<h2>Deta.space testing</h2>
<button on:click={save}>SAVE</button>
<button on:click={load}>LOAD</button>
<br />
{result}

<svelte:head>
	<title>Aziza Sydykova - Main page</title>
</svelte:head>
<main>
	<h1>Hi!✋ <br /> I'm Aziza a Software Engineer 💻 based in Kyrgyzstan</h1>
	<div class="icons">
		<div
			role="button"
			tabindex="0"
			on:keypress={() => {
				modalOpened.set(true);
			}}
			on:click={() => {
				modalOpened.set(true);
			}}
		>
			<div class="icon">
				<FaEnvelope />
			</div>
		</div>

		<a
			href="https://github.com/sydykova-auca-2021"
			aria-label="GitHub"
			target="_blank"
			rel="noopener noreferrer"
		>
			<div class="icon">
				<FaGithub />
			</div>
		</a>
		<a
			href="https://github.com/sydykova-auca-2021"
			aria-label="Linkedin"
			target="_blank"
			rel="noopener noreferrer"
		>
			<div class="icon">
				<FaLinkedin />
			</div>
		</a>
	</div>
</main>

<style>
	a {
		color: white;
		text-decoration: none;
	}
	main {
		text-align: center;
		padding: 0;
		margin: 0 auto;
		text-align: center;

		display: flex;
		flex-direction: column;
		height: calc(100vh - 80px - 88px);
		justify-content: center;
		align-items: center;
	}

	h1 {
		font-weight: 700;
	}

	main > h1 {
		margin: 50px 10px 0;
		font-size: 36px;
	}

	.icons {
		display: flex !important;
		justify-content: center !important;
		align-items: center;
		gap: 20px;
		cursor: pointer;
		font-size: 30px;
		display: flex;
		justify-content: space-between;
		max-width: 200px;
		margin: 50px auto 0;
	}

	.icon {
		cursor: pointer;
		transition: color 0.2s ease-in-out;
		width: 40px;
	}
	.icon:hover {
		color: #ca3c25;
	}

	@media (min-width: 900px) {
		main > h1 {
			font-size: 48px;
		}
	}

	@media (min-width: 600px) {
		main {
			max-width: none;
		}
	}
</style>
