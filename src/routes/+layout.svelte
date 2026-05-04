<script>
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';


  //  this section sets the origins for communication between
  //  parent (education platform) and iframe (jdilearning)
  //  for localhost (development) and production (Vercel)

    import { setContext } from 'svelte';
    //  localhost development
    //setContext("eduplatform", "http://localhost:5174");
    //setContext("jdilearning", "http://localhost:5173");
    //  Vercel deployment
    setContext("eduplatform", "https://eduplatform-sigma-nine.vercel.app");
    setContext("jdilearning", "https://jdilearning.vercel.app");

	let { children } = $props();
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>
{@render children()}
