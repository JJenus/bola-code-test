<template>
	<div class="flex Content-section">
		<SideBar />

		<div class="m-10">
			<div>
				<h2 class="text-2xl font-bold pb-6">
					Transaction({{ transactions.length }})
				</h2>
			</div>
			<div class="container shadow border roundedlg bg-white">
				<div class="action-call flex my-5">
					<button
						class="bg-transparent flex bg-color text-blue-700 font-semibold hover:text-black px-4 mx-4 border border-blue-500 hover:border-transparent rounded items-center"
					>
						<img src="../assets/plus.png" alt="menu" class="px-1" />
						Add income
					</button>
					<button
						class="bg-transparent flex text-red-500 font-semibold hover:text-black py-2 px-4 mx-4 border border-red-500 hover:border-transparent rounded items-center"
						@click="showModal"
					>
						<img
							src="../assets/plus (1).png"
							alt="menu"
							class="px-1"
						/>
						Add Expense
					</button>
					<button
						class="bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-black py-2 px-4 mx-4 border border-blue-500 hover:border-transparent rounded"
					>
						view debit
					</button>
					<input
						@keyup.enter="search()"
						v-model="searchVal"
						type="text"
						placeholder="enter your search here"
						class="rounded px-6 flex-1 text-gray-100 outline"
					/>
					<button
						class="bg-transparent flex bg-color text-black-500 font-semibold hover:text-black py-2 px-4 mx-4 hover:border-transparent rounded items-center"
					>
						<img
							src="../assets/ic-filter.png"
							alt="menu"
							class="px-1"
						/>Fitler
					</button>
				</div>
				<table class="table-fixed container">
					<thead>
						<tr class="py-6 border-t-1 h-10">
							<th class="text-base text-gray-500 font-medium">
								Date
							</th>
							<th class="text-base text-gray-500 font-medium">
								Customer
							</th>
							<th class="text-base text-gray-500 font-medium">
								Amount
							</th>
							<th class="text-base text-gray-500 font-medium">
								Payment Method
							</th>
							<th class="text-base text-gray-500 font-medium">
								Product
							</th>
							<th class="text-base text-gray-500 font-medium">
								Quantity
							</th>
						</tr>
						<tr
							class="text-base text-black bg-color font-normal py-6 h-10"
						>
							<th class="text-base text-black font-medium">
								Today
							</th>
							<th class="text-base text-black font-medium">
								#75,000
							</th>
							<th></th>
							<th></th>
							<th></th>
							<th></th>
						</tr>
					</thead>
					<tbody class="text-center text-black">
						<Transaction
							v-for="transaction in transactions"
							:transaction="transaction"
						/>
					</tbody>
				</table>

				<div
					class="pagination flex justify-center items-center h-12 py-3 my-3"
				>
					<a href="#">&laquo; Prev</a>
					<a href="#">1</a>
					<a class="active" href="#">2</a>
					<a href="#">3</a>
					<a href="#">4</a>
					<a href="#">5</a>
					<a href="#">6</a>
					<a href="#"> Next &raquo; </a>
				</div>
			</div>

			<ExpenseModal ref="modal" />
		</div>
	</div>
</template>

<script setup>
	import { ref, onMounted } from "vue";
	import axios from "axios";

	import ExpenseModal from "../components/CreateExpenseForm.vue";
	import SideBar from "../components/CreateSideBar.vue";
	import Transaction from "../components/Transaction.vue";

	const modal = ref(null);
	const transactionsEndpoint = ref(
		"https://dev1.noja.app/api/v1.0/cc/transactions"
	);
	const token = ref(
		"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJkYXRhIjp7InVzZXJJZCI6MSwibW9iaWxlIjoiODE2NDY0NDAwMyIsImJ1c2luZXNzSWQiOjEsImJ1c2luZXNzVXNlcklkIjoxLCJyb2xlSWQiOjEsInJvbGVUaXRsZSI6IkFjY291bnQgT3duZXIiLCJsYXN0TG9naW4iOiIyMDIyLTEwLTI2VDE3OjAyOjA2Ljc5OVoifSwiaWF0IjoxNjY2ODAzNzI2fQ.8A-qnjVqlBbiPdht3P9hvNzLAzl2Ow9OpId2OJmzQro"
	);

	console.log("loaded");

	const transactions = ref([]);
	const searchVal = ref("");
	const paginator = ref({
		action: "getTransaction",
		page: 1,
	});

	function nextPage(page) {
		if (paginator.value.action == "getTransaction") getTransactions();
		else if (paginator.value.action == "sort") sort();
		else if (paginator.value.action == "search") search();
	}

	function setTransactions(data) {
		transactions.value = data.reduce((p, c) => {
			p.push(...c.transactions);
			return p;
		}, []);

		console.log(transactions.value);
	}

	function getTransactions() {
		paginator.value.action = "getTransaction";

		const config = {
			method: "GET",
			url: transactionsEndpoint.value,
			headers: {
				Authorization: `Bearer ${token.value}`,
			},
			params: {
				page: paginator.value.page,
				limit: 100,
				sort: "purchase_date",
				sortDirection: "desc",
				searchTerm: searchVal.value,
			},
		};

		axios
			.request(config)
			.then((res) => {
				const data = res.data;
				// console.log("Transactions: ", data.data.transactions);
				if (data.code == 200) {
					setTransactions(data.data.transactions);
				}
			})
			.catch((error) => {
				console.log(error);
			})
			.finally(() => {
				// loadingPredictions.value = false;
			});
	}

	function search() {
		if (!searchVal.value || searchVal.value.length < 3) return;

		paginator.value.action = "search";

		const config = {
			method: "GET",
			url: transactionsEndpoint.value,
			headers: {
				Authorization: `Bearer ${token.value}`,
				params: {
					page: paginator.value.page,
					limit: 100,
					searchTerm: "f",
				},
			},
		};

		axios
			.request(config)
			.then((res) => {
				const data = res.data;
				// console.log("Transactions: ", data.data.transactions);
				if (data.code == 200) {
					setTransactions(data.data.transactions);
				}
			})
			.catch((error) => {
				console.log(error);
			})
			.finally(() => {
				// loadingPredictions.value = false;
			});
	}

	function sort() {
		paginator.value.action = "sort";

		const config = {
			method: "GET",
			url: transactionsEndpoint.value,
			headers: {
				Authorization: `Bearer ${token.value}`,
			},
			params: {
				page: paginator.value.page,
				limit: 100,
				sort: "purchase_date",
				sortDirection: "desc",
			},
		};

		axios
			.request(config)
			.then((res) => {
				const data = res.data;
				// console.log("Transactions: ", data.data.transactions);
				if (data.code == 200) {
					setTransactions(data.data.transactions);
				}
			})
			.catch((error) => {
				console.log(error);
			})
			.finally(() => {
				// loadingPredictions.value = false;
			});
	}

	function addExpense(message) {
		alert(message);
	}

	function showModal() {
		console.log(modal.value);
		modal.value.showModal();
	}

	onMounted(() => {
		getTransactions();
	});
</script>

<style scoped>
	@import url("../style.css");

	.Content-section {
		background-color: #f5f6fc;
	}

	.bg-color {
		background-color: #f9f9ff;
	}

	.pagination a {
		color: black;
		float: left;
		padding: 8px 16px;
		text-decoration: none;
		transition: background-color 0.3s;
	}

	.pagination a.active {
		background-color: dodgerblue;
		color: white;
	}

	.pagination a:hover:not(.active) {
		background-color: #ddd;
	}
</style>
