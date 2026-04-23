<script>
	import favicon from '$lib/assets/favicon.svg';

import "$lib/styles/reset.css"
import "$lib/styles/tokens.css"

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />

	<!-- satoshi font -->
	<link rel="preconnect" href="https://api.fontshare.com/"/>
	<link rel="preconnect" href="https://api.fontshare.com/" crossorigin>
	<link href="https://api.fontshare.com/v2/css?f[]=satoshi@1,2&display=swap" rel="stylesheet">

		<!-- inter font -->
<link rel="preconnect" href="https://fonts.bunny.net/">
<link rel="preconnect" href="https://fonts.bunny.net/" crossorigin>
<link href="https://fonts.bunny.net/css2?family=Inter:ital,opsz,wght@0,14..32,100..900;1,14..32,100..900&display=swap" rel="stylesheet">

<link rel="preconnect" href="https://rsms.me/">
<link rel="stylesheet" href="https://rsms.me/inter/inter.css">
</svelte:head>

{@render children()}
