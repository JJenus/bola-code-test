<script setup>
	const props = defineProps({
		transaction: {
			type: Object,
			required: true,
		},
	});

	function products() {
		const products = props.transaction.products.map((e) => e.name);
		return products;
	}

	function formatDate() {}

	function formatTime() {}
</script>

<template>
	<tr class="pb-3 h-10">
		<td class="text-base text-black font-medium">
			<input type="checkbox" class="pr-3" />08-Apr-22
			<br />
			<span class="text-xs text-gray-500">8.34pm</span>
		</td>
		<td class="text-base text-black font-medium">
			<span v-if="transaction.customer">
				{{ transaction.customer.name }}
			</span>
			<span v-else>
				{{ transaction.vendor.name }}
			</span>
		</td>
		<td
			:class="transaction.vendor ? 'text-red-500' : ''"
			class="text-base font-medium"
		>
			₦{{ transaction.amount_paid }}
		</td>
		<td>
			{{ transaction.payment_method }}
		</td>
		<td>
			<span v-if="transaction.products.length == 0">-</span>
			<span v-else>
				{{ products().join(", ") }}
			</span>
		</td>
		<td>
			<span v-if="transaction.products.length > 0">
				{{ products().length }}
			</span>
		</td>
	</tr>
	<tr v-for="payment in transaction.paymentHistories" class="h-10">
		<td>
			<small>{{ payment.paymentDate }}</small>
		</td>
		<td class="text-yellow-500">
			<span class="border">{{ payment.status }}</span>
		</td>
		<td class="text-yellow-500">
			{{ payment.amount }}
		</td>
		<td class="text-yellow-500">
			{{ payment.paymentMethod }}
		</td>
	</tr>
</template>
