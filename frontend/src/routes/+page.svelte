<script>
	import Counter from './Counter.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcome_fallback from '$lib/images/svelte-welcome.png';
	import { createAccordion, melt } from '@melt-ui/svelte';

	let message = '';

	// Fetch data from Laravel API
	async function fetchData() {
		const response = await fetch('http://vlc-project.test/be/api/example');
		const data = await response.json();
		message = data.message;
	}

	const {
    elements: { content, item, trigger, root },
    helpers: { isSelected },
  } = createAccordion({
    defaultValue: 'item-1',
  });
	const items = [
    {
      id: 'item-1',
      title: 'What is it?',
      description:
        'A collection of accessible & unstyled component builders for Svelte applications.',
    },
    {
      id: 'item-2',
      title: 'Can I customize it?',
      description: 'Totally, it is 100% stylable and overridable.',
    },
    {
      id: 'item-3',
      title: 'Svelte is awesome, huh?',
      description: 'Yes, and so are you!',
    },
  ];
 
  let className = '';
  export { className as class };

	fetchData();
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<h1 class="text-3xl font-bold underline">{message}</h1>

	
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
		width: 100%;
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
</style>
