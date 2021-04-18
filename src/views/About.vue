<template>
	<div class="about">
		<h1>This is an about page</h1>
		<div class="wrapper" v-if="loading">
			<!-- {{ productList }} -->
			<div v-if="(x, index) in productList" :key="x.id">{{ x.availableForSale }}</div>
		</div>
	</div>
</template>

<script>
	import Client from 'shopify-buy'

	import { ref } from 'vue'

	export default {
		setup() {
			const productList = ref(null)
			const loading = ref(false)

			const client = Client.buildClient({
				domain: 'buy3dprintedstuff-com.myshopify.com',
				storefrontAccessToken: 'bd6e62964d0ce7e3180d9e66deace0fb',
			})

			client.product.fetchAll().then(products => {
				let converToString = JSON.stringify(products)
				productList.value = JSON.parse(converToString)
				console.log(JSON.parse(converToString), 'qqq')
				loading.value = true
			})

			return { productList, client, loading }
		},
	}
</script>
