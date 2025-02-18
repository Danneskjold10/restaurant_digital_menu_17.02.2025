<script>
  let menuItems = [
    { name: "Classic Burger", solo: "€5.99", menu: "€7.99" },
    { name: "Cheese Burger", solo: "€6.49", menu: "€8.49" },
    { name: "Chicken Burger", solo: "€6.99", menu: "€8.99" }
  ];
</script>

<div class="container">
  <!-- Left Side: Image -->
  <div class="left">
    <img src="/commercial4.jpg" alt="Delicious Burger">
  </div>

  <!-- Right Side: Menu -->
  <div class="right">
    <!-- Menu Header -->
    <div class="menu-header">
      <div class="burger-title">Burger</div>
      <div class="solo-title">Solo</div>
      <div class="menu-title">Menu</div>
    </div>

    <!-- Menu List -->
    <div class="menu-list">
      {#each menuItems as item}
        <div class="menu-item">
          <div class="burger-name">{item.name}</div>
          <div class="solo-price">{item.solo}</div>
          <div class="menu-price">{item.menu}</div>
        </div>
      {/each}
    </div>
  </div>
</div>
