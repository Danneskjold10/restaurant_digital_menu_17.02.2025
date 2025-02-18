<script lang="ts">
  import { onMount } from "svelte";

  let showMenu = false;
  let showVideo = true; // Start with video
  let videoElement: HTMLVideoElement | null = null; // Reference to video

  const videoDuration = 10000; // 10 seconds
  const menuDuration = 30000; // 30 seconds

  function startCycle() {
    showVideo = true;
    showMenu = false;

    // Restart video every loop
    if (videoElement) {
      videoElement.currentTime = 0; // Reset video to start
      videoElement.play(); // Play video from beginning
    }

    // After 10 sec, switch to menu
    setTimeout(() => {
      showVideo = false;
      showMenu = true;
    }, videoDuration);

    // After 40 sec (10s video + 30s menu), restart cycle
    setTimeout(startCycle, videoDuration + menuDuration);
  }

  onMount(() => {
    videoElement = document.getElementById("promo-video") as HTMLVideoElement;
    startCycle();
  });

  let menuItems = [
    { name: "Classic Burger", priceSolo: "€5.99", priceMenu: "€8.99" },
    { name: "Cheese Deluxe", priceSolo: "€6.99", priceMenu: "€9.99" },
    { name: "BBQ Bacon Burger", priceSolo: "€7.49", priceMenu: "€10.49" },
    { name: "Veggie Burger", priceSolo: "€5.49", priceMenu: "€8.49" },
    { name: "Chicken Burger", priceSolo: "€6.49", priceMenu: "€9.49" },
    { name: "Spicy Chicken Burger", priceSolo: "€6.99", priceMenu: "€9.99" },
    { name: "Fish Burger", priceSolo: "€7.29", priceMenu: "€10.29" }
  ];
</script>

<style>
  /* Fullscreen Layout */
  html, body {
    margin: 0;
    padding: 0;
    width: 100vw;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
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
    opacity: 0;
    transition: opacity 1s ease-in-out;
  }

  .video-container.show {
    opacity: 1;
  }

  .video-container video {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  /* 📜 Menu List */
  .menu-container {
    width: 100%;
    text-align: left;
    padding: 20px;
    background-color: rgba(255, 255, 255, 0.95);
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0;
    transition: opacity 1s ease-in-out;
  }

  .menu-container.show {
    opacity: 1;
  }

  /* 📝 Headers */
  .menu-header {
    display: flex;
    justify-content: space-between;
    width: 100%;
    font-size: 2rem;
    font-weight: bold;
    padding-bottom: 10px;
    border-bottom: 2px solid black;
    margin-bottom: 20px;
    text-transform: uppercase;
  }

  .menu-header span {
    width: 32%;
    text-align: left;
  }

  /* 🍔 Menu Items */
  .menu-item {
    display: flex;
    justify-content: space-between;
    padding: 10px;
    font-size: 1.5rem;
    border-bottom: 1px solid #ccc;
  }

  .menu-item span {
    width: 32%;
    text-align: left;
  }

  /* 🖼 Bottom Image */
  .bottom-image {
    width: 100%;
    height: 60vh;
    object-fit: cover;
    position: absolute;
    bottom: 0;
    left: 0;
    opacity: 0;
    transition: opacity 1s ease-in-out;
  }

  .bottom-image.show {
    opacity: 1;
  }
</style>

<!-- 🎥 Show Video First -->
<div class="video-container {showVideo ? 'show' : ''}">
  <video id="promo-video" autoplay muted playsinline>
    <source src="/commercial4.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
</div>

<!-- 📜 Show Menu After 10s -->
<div class="menu-container {showMenu ? 'show' : ''}">
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

<!-- 🖼 Bottom Image (Appears with Menu) -->
<img src="/commercial4.jpg" alt="Burger" class="bottom-image {showMenu ? 'show' : ''}">
