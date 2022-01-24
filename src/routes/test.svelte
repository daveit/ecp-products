<script context="module">
    let prodleft = false;
</script>

<div class="content">
	<h1>Products Template</h1>

	<div class="grid justify-center mx-auto py-20">

		<div class="grid grid-cols-2 gap-8">

			<div class="px-12 py-14 shadow-md h-70 text-center">
				First
				<div class="justify-center mb-4">
                    <label>
                        <input type=checkbox bind:checked={prodleft}>
                        Select
                    </label>                        
				</div>
		    </div>

			<div class="px-12 py-14 shadow-md h-70 text-center ">
				Second
				<div class="justify-center mb-4">
                    <label>
                        <input type=checkbox disabled={!prodleft}>
                        Select
                    </label>                        
				</div>
		    </div>

        </div>
		
	</div>
</div>

<style>
</style>
