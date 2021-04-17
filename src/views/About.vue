<template>
	<div class="about">
		<h1>This is an about page</h1>
		<div class="wrapper">
			<!-- <div v-for="x in data" :key="x.id" class="single-product">
				<img src="" alt="" />
				<h2>{{ x }}</h2>
			</div> -->
		</div>
	</div>
</template>

<script>
	import Client from 'shopify-buy'

	import { ref } from 'vue'

	export default {
		setup() {
			const data = ref()

			const client = Client.buildClient({
				domain: 'buy3dprintedstuff-com.myshopify.com',
				storefrontAccessToken: 'bd6e62964d0ce7e3180d9e66deace0fb',
			})

			client.product.fetchAll().then(products => {
				// data.value = products.flatMap(x => x)
				console.log('a,', products[0])
			})

			return { data, client }
		},
	}
</script>
