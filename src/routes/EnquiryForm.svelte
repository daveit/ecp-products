<script>
    export let newProductNumber = "";
</script>

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
