<script>
	import Counter from './Counter.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcome_fallback from '$lib/images/svelte-welcome.png';
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" charset="UTF-8" />
</svelte:head>

<section>
	<h1>
		<span class="welcome">
			<picture>
				<source srcset={welcome} type="image/webp" />
				<img src={welcome_fallback} alt="Welcome" />
			</picture>
		</span>
		  شهدي العسل وسمائي الجميلة وبحري الذي أبحر ولا اغرق فيه
		<br>
		Happy Birthday my life love, I wish all the best and happy always with you,
		and I hope you a great day, that is Happy Birthday in my way !
	</h1>

	<h2>
		try editing <strong>شهدي العسل</strong>
	</h2>

	<Counter />
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
            color: #efab0b;
            text-align: center;
        }

        h2 {
            color: #67a1c1;
            text-align: center;
        }
	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}

	footer {
            background-color: #f5f5f5;
            padding: 20px;
            text-align: center;
            font-size: large;
        }
</style>
