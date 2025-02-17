<script lang="ts">
  export let menuItems = [
    { name: "Classic Burger", priceSolo: "€5.99", priceMenu: "€8.99", description: "A juicy beef patty with fresh lettuce, tomato, and cheese." },
    { name: "Cheese Deluxe", priceSolo: "€6.99", priceMenu: "€9.99", description: "Beef patty with double cheese, caramelized onions, and sauce." },
    { name: "BBQ Bacon Burger", priceSolo: "€7.49", priceMenu: "€10.49", description: "Smoky BBQ sauce, crispy bacon, and cheddar cheese." },
  ];

  let image = "/burger_4.jpg";
</script>

<style>
  .container {
    display: flex;
    flex-direction: row;
    height: 100vh;
    width: 100vw;
    background: white;
    color: black;
    overflow: hidden;
  }

  .left {
    width: 40%;
    display: flex;
    align-items: center;
    justify-content: center;
    background: black;
  }

  .left img {
    max-width: 90%;
    max-height: 90%;
    object-fit: contain;
  }

  .right {
    width: 60%;
    padding: 20px;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .menu-item {
    display: flex;
    justify-content: space-between;
    border-bottom: 2px solid gray;
    padding: 15px 0;
  }

  .menu-title {
    flex: 2;
    font-size: 2.5rem;
    font-weight: bold;
  }

  .menu-prices {
    flex: 1;
    text-align: right;
    font-size: 2rem;
    font-weight: bold;
  }

  .menu-prices span {
    display: block;
    margin-bottom: 5px;
  }
</style>

<div class="container">
  <!-- Left Side: Image -->
  <div class="left">
    <img src={image} alt="Menu Image">
  </div>

  <!-- Right Side: Menu List -->
  <div class="right">
    <!-- Table Header -->
    <div class="menu-item">
      <div class="menu-title">Burger</div>
      <div class="menu-prices">
        <span style="color: blue;">Solo</span>
        <span style="color: red;">Menu</span>
      </div>
    </div>

    <!-- Menu Items -->
    {#each menuItems as item}
      <div class="menu-item">
        <div class="menu-title">{item.name}</div>
        <div class="menu-prices">
          <span>{item.priceSolo}</span>
          <span>{item.priceMenu}</span>
        </div>
      </div>
    {/each}
  </div>
</div>
