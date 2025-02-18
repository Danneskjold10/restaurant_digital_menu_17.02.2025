<script>
  // Define your menu items
  const menuItems = [
    {
      name: "Classic Burger",
      description: "Juicy beef patty with fresh lettuce, tomato, and cheese.",
      soloPrice: "$9.99",
      menuPrice: "$12.99",
      image: "/burger_1112.png", // Same image for all items
    },
    {
      name: "Cheeseburger Deluxe",
      description: "Double beef patty with melted cheddar and special sauce.",
      soloPrice: "$12.99",
      menuPrice: "$15.99",
      image: "/burger_1112.png", // Same image for all items
    },
    {
      name: "Spicy Burger",
      description: "Spicy chicken patty with jalapeños and chipotle mayo.",
      soloPrice: "$11.99",
      menuPrice: "$14.99",
      image: "/burger_1112.png", // Same image for all items
    },
  ];
</script>

<style>
  /* Global styles for the menu */
  .menu {
    display: flex;
    flex-direction: column;
    gap: 20px;
    padding: 20px;
    background-color: #f8f8f8; /* Single background for the entire menu */
    height: 100vh; /* Full height for portrait display */
    font-family: Arial, sans-serif;
  }

  .menu-header {
    text-align: center;
    font-size: 2.5rem;
    font-weight: bold;
    color: #e67e22;
    margin-bottom: 20px;
  }

  .menu-item {
    display: flex;
    align-items: center;
    gap: 20px;
    padding: 15px;
    border-radius: 10px;
  }

  /* Alternate layout for the second row */
  .menu-item:nth-child(even) {
    flex-direction: row-reverse;
  }

  .item-details {
    flex: 1;
  }

  .item-name {
    font-size: 1.5rem;
    font-weight: bold;
    margin-bottom: 5px;
  }

  .item-description {
    font-size: 1rem;
    color: #555;
    margin-bottom: 10px;
  }

  .item-price {
    font-size: 1.2rem;
    color: #e67e22;
    font-weight: bold;
  }

  .item-price span {
    display: block;
    margin-bottom: 5px;
  }

  .item-image {
    width: 150px;
    height: 150px;
    object-fit: cover;
    border-radius: 10px;
  }
</style>

<div class="menu">
  <!-- Burger Header -->
  <div class="menu-header">Burgers</div>

  <!-- Menu Items -->
  {#each menuItems as item, index}
    <div class="menu-item">
      <div class="item-details">
        <div class="item-name">{item.name}</div>
        <div class="item-description">{item.description}</div>
        <div class="item-price">
          <span>Solo: {item.soloPrice}</span>
          <span>Menu: {item.menuPrice}</span>
        </div>
      </div>
      <img class="item-image" src={item.image} alt={item.name} />
    </div>
  {/each}
</div>