<script lang="ts">
  export let menuItems = [
    { name: "Classic Burger", priceSolo: "€5.99", priceMenu: "€8.99", description: "A juicy beef patty with fresh lettuce, tomato, and cheese." },
    { name: "Cheese Deluxe", priceSolo: "€6.99", priceMenu: "€9.99", description: "Beef patty with double cheese, caramelized onions, and sauce." },
    { name: "BBQ Bacon Burger", priceSolo: "€7.49", priceMenu: "€10.49", description: "Smoky BBQ sauce, crispy bacon, and cheddar cheese." },
  ];

  let images = ["/burger_4.jpg", "/sandwich_1.jpg", "/burger_1.jpg"];
  let currentImageIndex = 0;

  function changeImage() {
    currentImageIndex = (currentImageIndex + 1) % images.length;
  }

  setInterval(changeImage, 3000); // Change image every 3 seconds
</script>

<div class="min-h-screen bg-white text-black p-6 text-center flex flex-col items-center">
  <img src={images[currentImageIndex]} alt="Menu Header" class="w-3/4 max-h-80 object-cover rounded-lg mb-6 transition-opacity duration-500 ease-in-out">
  
  <div class="w-full max-w-md mx-auto">
    <h1 class="text-4xl font-bold mb-4">Burger Menu</h1>
    <div class="flex flex-col gap-4">
      {#each menuItems as item}
        <div class="bg-gray-200 p-4 rounded-lg shadow-lg">
          <h2 class="text-2xl font-semibold">{item.name}</h2>
          <p class="text-gray-600">{item.description}</p>
          <div class="mt-2 flex justify-between">
            <span class="text-lg font-bold">Solo: {item.priceSolo}</span>
            <span class="text-lg font-bold">Menu: {item.priceMenu}</span>
          </div>
        </div>
      {/each}
    </div>
  </div>
</div>
