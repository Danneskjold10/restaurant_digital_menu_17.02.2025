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
    justify-content: center; /* Center vertically */
    align-items: center; /* Center horizontally */
    gap: 20px;
    padding: 20px;
    background-color: #ffffff; /* Updated background color */
    height: 100vh; /* Full height for portrait display */
    width: 100vw; /* Full width for portrait display */
    font-family: Arial, sans-serif;
    box-sizing: border-box; /* Ensure padding doesn't overflow */
  }

  .menu-header {
    text-align: center;
    font-size: 3rem; /* Larger font size for header */
    font-weight: bold;
    color: #e67e22; /* Orange color for header */
    margin-bottom: 20px;
  }

  .menu-item {
    display: flex;
    align-items: center;
    gap: 20px;
    padding: 15px;
    border-radius: 10px;
    width: 90%; /* Adjust width to fit screen */
    max-width: 800px; /* Limit maximum width */
  }

  /* Alternate layout for the second row */
  .menu-item:nth-child(even) {
    flex-direction: row-reverse;
  }

  .item-details {
    flex: 1;
  }

  .item-name {
    font-size: 2rem; /* Larger font size for item name */
    font-weight: bold;
    margin-bottom: 10px;
  }

  .item-description {
    font-size: 1.2rem; /* Larger font size for description */
    color: #555;
    margin-bottom: 10px;
  }

  .price-tag {
    display: inline-block;
    padding: 5px 10px;
    border-radius: 5px;
    font-size: 1.2rem;
    font-weight: bold;
    color: white;
    margin-bottom: 5px;
  }

  .solo-price {
    background-color: #2e7d32; /* Green for solo price */
  }

  .menu-price {
    background-color: #d32f2f; /* Red for menu price */
  }

  .item-image {
    width: 200px; /* Larger image size */
    height: 200px; /* Larger image size */
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
          <div class="price-tag solo-price">Solo: {item.soloPrice}</div>
          <div class="price-tag menu-price">Menu: {item.menuPrice}</div>
        </div>
      </div>
      <img class="item-image" src={item.image} alt={item.name} />
    </div>
  {/each}
</div>