<script>
	import { fade } from 'svelte/transition';
	//import EnquiryForm from './EnquiryForm.svelte';
	//import { slide } from 'svelte/transition';
	//import { quintOut } from 'svelte/easing';
	//import { form, field } from 'svelte-forms';
  	//import { required } from 'svelte-forms/validators';

  	//const name = field('name', [required()]);
  	//const myForm = form(name);

	//import { browser, dev } from '$app/env';

	// we don't need any JS on this page, though we'll load
	// it in dev so that we get hot module replacement...
	//export const hydrate = dev;

	// ...but if the client-side router is already loaded
	// (i.e. we came here from elsewhere in the app), use it
	//export const router = browser;

	// since there's no dynamic data here, we can prerender
	// it so that it gets served as a static asset in prod
	//export const prerender = true;

	//let yes = false;
	//let isShadowed = false;
	//let products = 1;
	//let partNumberForm = "Enquiry for part number: "
	//let productNames = [
	//	'Dual',
	//	'Left',
	//	'Right'
	//];


	// function changeDual(event) {
	// 	dualImage = !dualImage;
    // 	rightImage = !rightImage;
	// }
	// function changeLeft(event) {
	// 	leftImage = !leftImage;
	// 	//rightImage = !rightImage;
	// }

	// function changeRight(event) {
	// 	rightImage = !rightImage;
	// 	leftImage = !leftImage;
	// }
	//let dualImage = false;
	//let leftImage = false;
	//let rightImage = false;


	let selected = 0;
	let prodPrefix = "";
	let prodArmCable = "";
	let prodStrobe = "";
	let prodRemIso = "";
	let prodEntries = "";
    let newProductNumber = "";
	let noOtherSelections = false;
	let greyDual = false;
	let greyLeft = false;
	let greyRight = false;
	let productSelection = [];
	let armChecked = false;
	let remChecked = false;
	
	const entriesChange = (event) => {
		selected = event.currentTarget.value;
		if (selected == 1 ) {
			prodEntries = "-2E";
		}
		if (selected == 2 ) {
			prodEntries = "-3E";
		}
		if (selected == 3 ) {
			prodEntries = "-4E";
		}
	}

	const strobeChange = (event) => {
		selected = event.currentTarget.value;
		if (selected == 1 ) {
			prodStrobe = "-S1";
		}
		if (selected == 2 ) {
			prodStrobe = "-S2";
		}
		if (selected == 3 ) {
			prodStrobe = "-S3";
		}
		if (selected == 4 ) {
			prodStrobe = "-S4";
		}
		if (selected == 5 ) {
			prodStrobe = "-S5";
		}
		if (selected == 6 ) {
			prodStrobe = "-S6";
		}
	}

	const dualSelected = () => {
		greyLeft = !greyLeft;
		greyRight = !greyRight;
		prodPrefix = "STP-P-2";
	}

	const leftSelected = () => {
		greyDual = !greyDual;
		greyRight = !greyRight;
		prodPrefix = "STP-P-2-LH";
	}

	const rightSelected = () => {
		greyDual = !greyDual;
		greyLeft = !greyLeft;
		prodPrefix = "STP-P-2-RH";
	}

	const armouredClicked = () => {
		//prodArmCable = "-AC-2E";
		noOtherSelections = !noOtherSelections;
		armChecked = !armChecked;
		if (armChecked == true) {
			prodArmCable = "-AC-2E";
			prodStrobe = "";
			prodEntries = "";
			prodRemIso = "";
			remChecked = false;
		}
			else {
				prodArmCable = "";
		}
	}

	const remClicked = () => {
		remChecked = !remChecked;
		if (remChecked == true) {
			prodRemIso = "-REM";
		}
			else {
				prodRemIso = "";
		}
	}

	$: newProductNumber = (prodPrefix + prodArmCable + prodStrobe + prodRemIso + prodEntries);

</script>

<svelte:head>
	<title>Products</title>
</svelte:head>

<div class="content">

	<div class="grid justify-center mx-auto py-7 mb-10">
		<h1 class="mb-2">STANDARD PLASTIC – NON TENSION – EMERGENCY STOP PULL WIRE SWITCH</h1>

		<div class="grid grid-cols-1 gap-8 sm:grid-cols-2 md:grid-cols-3">

			<div class="px-10 py-5 shadow-2xl h-45 text-center text-blue-600 font-bold text-2xl">
				<img src="dual-non-tension-sp-1.png" alt="Dual" class:gray={greyDual}>
				{#if productSelection.length === 0 || productSelection.includes("Dual")}
 				<label transition:fade="{{delay: 350, duration: 500}}">
					<input type=checkbox on:click="{dualSelected}" name="productselection" bind:group={productSelection} value="Dual">
					Dual
				</label>
				{/if}
		    </div>

			<div class="px-10 py-5 shadow-2xl h-45 text-center text-blue-600 font-bold text-2xl">
				<img src="lh-non-tension-sp-1.png" alt="Left" class:gray={greyLeft}>
				<!-- checkbox for Left -->
				{#if productSelection.length === 0 || productSelection.includes("Left")}
				<label transition:fade="{{delay: 350, duration: 500}}">
					<input type=checkbox on:click="{leftSelected}" name="productselection" bind:group={productSelection} value="Left">
					Left
				</label>
				{/if}
		    </div>

			<div class="px-10 py-5 shadow-2xl h-45 text-center text-blue-600 font-bold text-2xl">
				<img src="rh-non-tension-sp-1.png" alt="Right" class:gray={greyRight}>
				<!-- checkbox for right -->
				{#if productSelection.length === 0 || productSelection.includes("Right")}
				<label transition:fade="{{delay: 350, duration: 500}}">
					<input type=checkbox on:click="{rightSelected}" name="productselection" bind:group={productSelection} value="Right">
					Right
				</label>
				{/if}
		    </div>

        </div>

        <div class="text-center mt-5">
			<h2 class="text-gray-600 font-bold text-2xl">{ newProductNumber }</h2>
		</div>

		<div class="grid justify-center mx-auto">
			<p class="to-blue-800 font-bold"><span class="text-red-900 uppercase">Additional Options</span> - Some options may not be available together<br>e.g. additonal entries are not available with armoured cable gland sockets</p>
			<div class="text-center mt-5 radios">
				<label>
					<h3>Armoured Cable Gland Sockets?</h3>
					<input type=checkbox on:click={armouredClicked} name="armoured" value="armoured" checked={armChecked}>
					
				</label>
			</div>

			{#if !noOtherSelections}
			<div transition:fade="{{delay: 350, duration: 500}}" class="text-center mt-5 radios">
				<h3>Strobe Options</h3>
				<label>
					<input type=radio on:change={strobeChange} name="strobe" value={1}>
					Red - 10-100V DC
					<br>
					<input type=radio on:change={strobeChange} name="strobe" value={2}>
					Red - 110V AC
					<br>
					<input type=radio on:change={strobeChange} name="strobe" value={3}>
					Red - 240V AC
					<br>
					<input type=radio on:change={strobeChange} name="strobe" value={4}>
					Amber - 10-100V DC
					<br>
					<input type=radio on:change={strobeChange} name="strobe" value={5}>
					Amber - 110V AC
					<br>
					<input type=radio on:change={strobeChange} name="strobe" value={6}>
					Amber - 240V AC
				</label>
			</div>
			{/if}

			{#if !noOtherSelections}
			<div transition:fade="{{delay: 350, duration: 500}}" class="text-center mt-5 radios">
				<h3>Remote Isolation?</h3>
				<label>
					<input type=checkbox on:click={remClicked} name="armoured" checked={remChecked}>
				</label>
			</div>
			{/if}

			{#if !noOtherSelections}
			<div class="text-center mt-5 radios" transition:fade="{{delay: 350, duration: 500}}">
				<h3>Number of Entries</h3>
				<label>
					<input type=radio on:change={entriesChange} name="armoured" value={1}>
					2 Entries
					<input type=radio on:change={entriesChange} name="armoured" value={2}>
					3 Entries
					<input type=radio on:change={entriesChange} name="armoured" value={3}>
					4 Entries
				</label>
			</div>
			{/if}

	</div>
		
 	<div class="px-52 mb-16 mt-8">
		<hr>
		<h3 class=" text-gray-400 text-1xl text-center">Enquiry Form</h3>

		<form>
			<div class="mb-6">
				<label for="productcode" class="text-sm font-medium text-gray-900 block mb-2 dark:text-gray-300">Product Code</label>
				<input type="text" id="productcode" class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" value="{newProductNumber}" disabled readonly>
			</div>

			<div class="mb-6">
				<label for="name" class="text-sm font-medium text-gray-900 block mb-2 dark:text-gray-300">Your name</label>
				<input type="text" id="name" class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="your name" required>
			</div>


			<div class="mb-6">
				<label for="email" class="text-sm font-medium text-gray-900 block mb-2 dark:text-gray-300">Your Email</label>
				<input type="email" id="email-adress-icon" class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5  dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="example@company.com">
			</div>

			<div class="mb-6">
				<label for="phone" class="text-sm font-medium text-gray-900 block mb-2 dark:text-gray-300">Your phone#</label>
				<input type="text" id="phone" class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="your phone#" required>
			</div>

			<div class="mb-6">
				<label for="dealer" class="text-sm font-medium text-gray-900 block mb-2 dark:text-gray-400">Select your dealer</label>
				<select id="dealer" class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
					<option>Select your supplier</option>
					<option>R & D Technology QLD</option>
					<option>Kinder & Co. Pty. Ltd VIC</option>
					<option>R & D Technology NSW</option>
					<option>Power Control Products SA</option>
					<option>Power Control Products NT</option>
					<option>Power Control Products TAS</option>
					<option>Power Control Products WA</option>
				</select>
				</div>
			<button type="submit" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Submit</button>
		</form>
	</div>

</div>

</div>


<style>
	.content {
		width: 100%;
		/* max-width: var(--column-width); */
		/* margin: var(--column-margin-top) auto 0 auto; */
	}

	p {
		font-size: 16px;
	}

	h1 {
		font-size: 28px;
	}

	h2 {
		font-size: 24px;
		text-align: center;
		padding-bottom: 12px;
	}

	h3 {
		font-size: 22px;
	}

	.gray {
		filter: grayscale(100%);
	}

</style>