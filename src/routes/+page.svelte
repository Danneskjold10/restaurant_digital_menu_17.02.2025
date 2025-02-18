<script lang="ts">
  import { onMount } from "svelte";

  let showMenu = false;
  let cycleCount = 0;

  let menuItems = [
    { name: "Classic Burger", priceSolo: "€5.99", priceMenu: "€8.99" },
    { name: "Cheese Deluxe", priceSolo: "€6.99", priceMenu: "€9.99" },
    { name: "BBQ Bacon Burger", priceSolo: "€7.49", priceMenu: "€10.49" }
  ];

  // Cycle through the commercial and menu list
  onMount(() => {
    setInterval(() => {
      cycleCount++;
      showMenu = !showMenu;  // Toggle between commercial and menu list

      // Reset after 5 cycles (5 full commercial/menu loops)
      if (cycleCount >= 5) {
        cycleCount = 0;
      }
    }, 15000); // Switch every 15 seconds (10s video + 5s transition time)
  });
</script>

<style>
  /* Full screen layout */
  html, body {
    margin: 0;
    padding: 0;
    width: 100vw;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    background-color: #fff;
    overflow: hidden;
  }

  /* 🎥 Fullscreen Video */
  .video-container {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    z-index: 1;
  }

  .video-container video {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  /* 📜 Menu List (TOP) */
  .menu-container {
    width: 100%;
    text-align: left;
    padding: 20px;
    background-color: rgba(255, 255, 255, 0.95);
    position: absolute;
    top: 0;
    left: 0;
    z-index: 2;
    transition: opacity 0.5s ease-in-out;
  }

  /* 📝 Headers */
  .menu-header {
    display: flex;
    justify-content: flex-start;
    width: 100%;
    font-size: 2rem;
    font-weight: bold;
    padding-bottom: 10px;
    border-bottom: 2px solid black;
  }

  /* 🍔 Menu Items */
  .menu-item {
    display: flex;
    justify-content: flex-start;
    padding: 10px;
    font-size: 1.5rem;
    border-bottom: 1px solid #ccc;
  }

  .menu-item span {
    width: 33%;
    text-align: left;  /* Left-align text */
  }

  /* 🖼 Image at the bottom */
  .bottom-image {
    width: 100%;
    height: 40vh;
    object-fit: cover;
    position: absolute;
    bottom: 0;
    left: 0;
    z-index: 2;
  }
</style>

<!-- 🎥 Show Video First -->
{#if !showMenu}
  <div class="video-container">
    <video autoplay muted playsinline>
      <source src="/video.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
{/if}

<!-- 📜 Show Menu After 10s -->
{#if showMenu}
  <div class="menu-container">
    <div class="menu-header">
      <span>Burger</span>
      <span>Solo</span>
      <span>Menu</span>
    </div>

    {#each menuItems as item}
      <div class="menu-item">
        <span>{item.name}</span>
        <span>{item.priceSolo}</span>
        <span>{item.priceMenu}</span>
      </div>
    {/each}
  </div>

  <!-- 🖼 Bottom Image -->
  <img src="/commercial4.jpg" alt="Burger" class="bottom-image">
{/if}
