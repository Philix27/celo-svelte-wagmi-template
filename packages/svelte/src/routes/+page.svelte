<script lang="ts">
	import { Toaster } from 'svelte-french-toast/dist';
	import Network from '../components/Network.svelte';
	import SignMessage from '../components/SignMessage.svelte';
	import Wallet from '../components/Wallet.svelte';
	import { account, modal, disconnect } from '../lib/client';
	import Button from '../components/Button.svelte';

	function connectWallet() {
		modal.open({ view: 'Connect' });
	}
</script>

<div class="md:md-0 w-full flex items-center justify-center">
	<div class="w-[75%] my-5 flex items-center justify-center flex-col">
		<div class="h1">There you go... a canvas for your next Celo project!</div>
		{$account.isConnected ? 'Hey' : 'No'}
		{#if $account.isConnected}
			<div class="pt-10 md:pt-0 mx-0 flex flex-col items-center justify-center">
				<Button onclick={disconnect} variant="destructive">Disconnect</Button>
				<p>Your address:</p>
				<p>{$account.address}</p>
				Extra wallet metadata available when present
				<Network />
				 <Wallet />
				<!-- <Wallet />
				<SignMessage /> -->
			</div>
		{:else}
			<div>
				No Wallet Connected
				<Button onclick={connectWallet}>Connect</Button>
			</div>
		{/if}
	</div>
</div>

<Toaster />
