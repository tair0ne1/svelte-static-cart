<script>
	import Product from './Product.svelte';
	import Button from './Button.svelte';
	import Cart from './Cart.svelte';

	let title = '';
	let price = 0;
	let description = '';

	let products = [];
	let cartItems = [];

	function createProduct() {
		const newProduct = {
			title,
			price,
			description
		};

		products = products.concat(newProduct);
	}

	function addToCart(event) {
		const title = event.detail;
		cartItems = cartItems.concat({
			... products.find(prod => prod.title === title)
		});
	}
</script>

<style>
	section {
		width: 30rem;
		margin: auto;
	}

	input,
	label,
	textarea {
		width: 100%;
	}
</style>

<section>
	<Cart items={cartItems}/>
</section>

<hr>

<section>
	<div>
		<label for="title">Title</label>
		<input type="text" id="title" bind:value={title}/>
	</div>
	<div>
		<label for="price">Price</label>
		<input type="number" id="price" bind:value={price}/>
	</div>
	<div>
		<label for="description">Description</label>
		<textarea rows="3" id="description" bind:value={description}/>
	</div>

	<Button on:click="{createProduct}">Create Product</Button>

</section>

<section>
{#if products.length === 0}
	<p>No products were added yet!</p>
	{:else}
	{#each products as product}
		<Product
			title={product.title}
			price={product.price}
			description={product.description}
			on:addCart={addToCart}
		/>
	{/each}
{/if}
</section>