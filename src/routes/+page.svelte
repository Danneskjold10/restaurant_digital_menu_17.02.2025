<script lang="ts">
  import { onMount } from "svelte";

  let showMenu = false;
  let cycleCount = 0;
  let text = "";
  let textCycleTime = 10000; // Time for each cycle in milliseconds
  let currentTextIndex = 0;
  let textArray = ["Delicious", "More Delicious", "Much More Delicious"];
  
  let menuItems = [
    { name: "Classic Burger", priceSolo: "€5.99", priceMenu: "€8.99" },
    { name: "Cheese Deluxe", priceSolo: "€6.99", priceMenu: "€9.99" },
    { name: "BBQ Bacon Burger", priceSolo: "€7.49", priceMenu: "€10.49" },
    { name: "Veggie Burger", priceSolo: "€5.49", priceMenu: "€8.49" },
    { name: "Chicken Burger", priceSolo: "€6.49", priceMenu: "€9.49" },
    { name: "Spicy Chicken Burger", priceSolo: "€6.99", priceMenu: "€9.99" },
    { name: "Fish Burger", priceSolo: "€7.29", priceMenu: "€10.29" }
  ];

  // Cycle between video and menu list every 10 seconds
  onMount(() => {
    let videoInterval = setInterval(() => {
      cycleCount++;
      showMenu = !showMenu;

      // Switch back to the video after 10 seconds
      if (cycleCount >= 2) {
        cycleCount = 0;
        showMenu = false;
      }
    }, textCycleTime); // 10 seconds for video/menu switch

    let textInterval = setInterval(() => {
      if (!showMenu) {
        // Display the current text and move to the next
        text = textArray[currentTextIndex];

        currentTextIndex++;
        if (currentTextIndex >= textArray.length) {
          currentTextIndex = 0;
        }
      }
    }, 2000); // Change text every 2 seconds
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
    z-index: 1;
  }

  .video-container video {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  /* Text in front of the video */
  .video-text {
    position: absolute;
    top: 40%;
    left: 50%;
    transform: translateX(-50%);
    font-weight: bold;
    color: #fff;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7);
    z-index: 2;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 3rem;
    animation: slideText 10s ease-in-out infinite, textAnimation 10s ease-in-out infinite;
  }

  /* Animation for text change */
  @keyframes slideText {
    0%, 100% {
      opacity: 0;
    }
    33% {
      opacity: 1;
    }
    66% {
      opacity: 1;
    }
  }

  /* Text styling for each phase */
  @keyframes textAnimation {
    0%, 100% {
      transform: scale(1);
      color: #fff;
    }
    33% {
      transform: scale(1.1);
      color: #f39c12;
    }
    66% {
      transform: scale(1.2);
      color: #e74c3c;
    }
  }

  /* Text Styles */
  .video-text span.delicious {
    font-size: 3rem;
    font-family: 'Arial', sans-serif;
  }
  
  .video-text span.more-delicious {
    font-size: 4rem;
    font-family: 'Verdana', sans-serif;
  }
  
  .video-text span.much-more-delicious {
    font-size: 5rem;
    font-family: 'Georgia', serif;
    font-weight: bolder;
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
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    opacity: 0;
    transition: opacity 2s ease-in-out;
  }

  /* Show menu container when it's time for the menu */
  .menu-container.visible {
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
    width: 32%; /* Make space for the columns */
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
    text-align: left; /* Left-align text */
  }

  /* 🖼 Image at the bottom */
  .bottom-image {
    width: 100%;
    height: 60vh;
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
      <source src="/commercial4.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <!-- Text Over the Video -->
  <div class="video-text">
    {#if text === 'Delicious'}
      <span class="delicious">{text}</span>
    {:else if text === 'More Delicious'}
      <span class="more-delicious">{text}</span>
    {:else if text === 'Much More Delicious'}
      <span class="much-more-delicious">{text}</span>
    {/if}
  </div>
{/if}

<!-- 📜 Show Menu After 10s -->
{#if showMenu}
  <div class="menu-container visible">
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
