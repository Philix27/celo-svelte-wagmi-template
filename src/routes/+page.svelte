<!-- 
	YOU CAN DELETE EVERYTHING IN THIS PAGE EXCEPT 
	-	<Toaster /> 
-->
<script lang="ts">
	import { account } from '$lib/web3modal';
	import { Toaster } from 'svelte-french-toast';
	import Network from '../components/Network.svelte';
	import SignMessage from '../components/SignMessage.svelte';
	import SignTypeData from '../components/SignTypeData.svelte';
	import Transaction from '../components/Transaction.svelte';
	import Wallet from '../components/Wallet.svelte';
</script>

<div class="md:md-0 w-full flex items-center justify-center">
	<div class="w-[75%] my-5">
		{#if $account.isConnected}
			<div class="pt-10 md:pt-0 mx-0">
				<h2 class="h2 text-center grid-span-1 md:col-span-3 pt-2">
					Sign a message from the current wallet.
				</h2>
				<div class="grid grid-cols-1 md:grid-cols-3 gap-6 text-center pt-5 md:pt-0">
					<div class="grid-span-1 md:col-span-3"></div>
					<div class="grid-span-1 md:col-span-3">
						<Network />
					</div>
					Extra wallet metadata available when present
					<div class="col-span-3">
						<Wallet />
					</div>

					<div class="col-span-3"><SignMessage /></div>
					<div class="col-span-3"><SignTypeData /></div>
					<div class="col-span-3"><Transaction /></div>
				</div>
			</div>
		{/if}
	</div>
</div>

<Toaster />
