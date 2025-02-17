<script lang="ts">
  export let menuItems = [
    { name: "Classic Burger", priceSolo: "€5.99", priceMenu: "€8.99", description: "A juicy beef patty with fresh lettuce, tomato, and cheese." },
    { name: "Cheese Deluxe", priceSolo: "€6.99", priceMenu: "€9.99", description: "Beef patty with double cheese, caramelized onions, and sauce." },
    { name: "BBQ Bacon Burger", priceSolo: "€7.49", priceMenu: "€10.49", description: "Smoky BBQ sauce, crispy bacon, and cheddar cheese." },
  ];

  let image = "/commercial4.jpg"; // Single image
</script>

<div class="flex flex-row h-screen w-full bg-white text-black">
  <!-- Left Side: Image -->
  <div class="w-1/2 h-full flex items-center justify-center bg-gray-100">
    <img src={image} alt="Menu Image" class="h-auto w-full max-h-full object-cover rounded-lg shadow-lg">
  </div>

  <!-- Right Side: Menu List -->
  <div class="w-1/2 h-full p-6 flex flex-col justify-center">
    <h1 class="text-4xl font-bold mb-4 text-center">Burger Menu</h1>

    <!-- Menu Table -->
    <div class="bg-gray-200 p-4 rounded-lg shadow-lg">
      <!-- Table Header -->
      <div class="grid grid-cols-3 font-bold text-lg border-b pb-2">
        <span class="text-left">Burger</span>
        <span class="text-center">Solo</span>
        <span class="text-right">Menu</span>
      </div>

      <!-- Menu Items -->
      {#each menuItems as item}
        <div class="grid grid-cols-3 py-3 border-b last:border-none">
          <span class="text-left">{item.name}</span>
          <span class="text-center">{item.priceSolo}</span>
          <span class="text-right">{item.priceMenu}</span>
        </div>
      {/each}
    </div>
  </div>
</div>
