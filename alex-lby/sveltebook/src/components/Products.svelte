<script>
    import { products, cart } from "../stores";
    import Cart from "./Cart.svelte";
    import Button from "./Button.svelte";

    // export let location;

    const addToCart = (product) => {
        for(let item of $cart) {
            if(item.id === product.id) {
                product.quantity += 1;
                $cart = $cart;
                return;
            }
        }
        $cart = [...$cart, product]
    }
</script>


<style>
    /* …styles go here… */
</style>

<div class="product-list">
    {#each $products as product}
      <div>
        <div><img src="{product.image}" alt="Coffee"></div>
        <h4><a href="product/{product.id}">{product.name}</a></h4>
        <div class="cta">
          <p>${product.price}</p>
          <Button on:click={() => addToCart(product)}>
            Add to cart
          </Button>
        </div>
      </div>
    {/each}
  </div>
  <Cart />