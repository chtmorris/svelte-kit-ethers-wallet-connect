<script lang="ts">
	import {
		accountChainId,
		connected,
		connectMetamask,
		connectWalletConnect,
		disconnect,
		walletAddress
	} from '$lib/stores/provider';
	import { balanceOnBlock } from '$lib/stores/state';
	import { formatEther } from 'ethers/lib/utils';
</script>

<main class="flex flex-col p-10 w-screen h-screen items-center gap-5 font-serif">

	<nav class="bg-white dark:bg-gray-900 fixed w-full z-20 top-0 left-0 border-b border-gray-200 dark:border-gray-600">
		<div class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4">
			<div class="flex items-center">
				<img src="https://flowbite.com/docs/images/logo.svg" class="h-8 mr-3" alt="Flowbite Logo">
				<span class="self-center text-2xl font-semibold whitespace-nowrap dark:text-white">Svelte Ethers Template</span>
			</div>
			<div class="flex md:order-2">
				<button on:click={connectWalletConnect} type="button" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-4 py-2 text-center mr-3 md:mr-0 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Connect Wallet</button>
				<button data-collapse-toggle="navbar-sticky" type="button" class="inline-flex items-center p-2 text-sm text-gray-500 rounded-lg md:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600" aria-controls="navbar-sticky" aria-expanded="false">
					<span class="sr-only">Open main menu</span>
					<svg class="w-6 h-6" aria-hidden="true" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 10a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 15a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1z" clip-rule="evenodd"></path></svg>
				</button>
			</div>
			<div class="items-center justify-between hidden w-full md:flex md:w-auto md:order-1" id="navbar-sticky">
				<ul class="flex flex-col p-4 md:p-0 mt-4 font-medium border border-gray-100 rounded-lg bg-gray-50 md:flex-row md:space-x-8 md:mt-0 md:border-0 md:bg-white dark:bg-gray-800 md:dark:bg-gray-900 dark:border-gray-700">
					<li>
						<a href="#" class="block py-2 pl-3 pr-4 text-white bg-blue-700 rounded md:bg-transparent md:text-blue-700 md:p-0 md:dark:text-blue-500" aria-current="page">Home</a>
					</li>
					<li>
						<a href="#" class="block py-2 pl-3 pr-4 text-gray-900 rounded hover:bg-gray-100 md:hover:bg-transparent md:hover:text-blue-700 md:p-0 md:dark:hover:text-blue-500 dark:text-white dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent dark:border-gray-700">Page 2</a>
					</li>
					<li>
						<a href="#" class="block py-2 pl-3 pr-4 text-gray-900 rounded hover:bg-gray-100 md:hover:bg-transparent md:hover:text-blue-700 md:p-0 md:dark:hover:text-blue-500 dark:text-white dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent dark:border-gray-700">Page 3</a>
					</li>
				</ul>
			</div>
		</div>
	</nav>

	<h1 class="text-5xl text-black font-bold mt-20">Svelte Ethers Template</h1>

	<p>A template of useful components for Svelte Kit + Ethers + Wallet Connect</p>

	<section class="flex flex-col p-10 items-start gap-5 border-2 rounded-xl mt-20">
		<h1 class="text-2xl text-black font-bold">Wallet and Provider</h1>
		<h2 class="text-xl text-black font-semibold">$connected: {$connected}</h2>
		<h2 class="text-xl text-black font-semibold">$walletAddress: {$walletAddress}</h2>
		<h2 class="text-xl text-black font-semibold">
			$accountChainId: {JSON.stringify($accountChainId)}
		</h2>
		<button
			on:click={connectMetamask}
			class="p-3 rounded-xl text-xl bg-black text-white font-semibold hover:scale-[1.05] transition transition-200"
			>Connect via MetaMask</button
		>
		<button
			on:click={connectWalletConnect}
			class="p-3 rounded-xl text-xl bg-black text-white font-semibold hover:scale-[1.05] transition transition-200"
			>Connect via WalletConnect</button
		>
		<button
			on:click={disconnect}
			class="p-3 rounded-xl text-xl bg-black text-white font-semibold hover:scale-[1.05] transition transition-200"
			>Disconnect</button
		>
	</section>
	<section class="flex flex-col p-10 items-start gap-5 border-2 rounded-xl">
		<h1 class="text-2xl text-black font-bold">Sync contract state on block, event or interval</h1>
		<p class="text-md text-black font-semibold">
			Set In '$lib/globalState.ts', will load as long as a store is used from '$lib/stores/state.ts'
			or you import the globalState in the root of your project with 'import "$lib/globalState";'
		</p>
		<h2 class="text-xl text-black font-semibold">
			$balanceOnBlock: {formatEther($balanceOnBlock)} ETH
		</h2>
	</section>

</main>
