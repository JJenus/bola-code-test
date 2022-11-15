<template>
  <form>
    <div>
      <div>
        <label for="amountSpent">Amount Spent</label>
        <input type="number" id="amountSpent" />
      </div>

      <div>
        <label for="paymentMethod">Payment Method</label>
        <select id="paymentMethod">
          <option>Cash</option>
          <option>Debit Card</option>
          <option>Bank transfer</option>
        </select>
        <div>
          <label for="date">Date Of Expense</label>
          <input type="date" id="date" />
        </div>
      </div>

      <div>
        <input type="text" placeholder="Select who you paid to" />
      </div>

      <div>
        <label for="expenseCategory">Expense Category</label>
        <select id="expenseCategory">
          <option>Select a category</option>
          <option>Cash</option>
          <option>Debit Card</option>
          <option>Bank transfer</option>
        </select>
      </div>

      <div></div>

      <div>
        <label for="optionalText">What was this payment for? (optional)</label>
        <textarea id="optionalText" placeholder="e.g new purchase of items" />
      </div>
    </div>

    <div>
      <div>
        <input type="checkbox" />
        <p>Create new after submit</p>
      </div>

      <button><p>Save</p></button>
    </div>
  </form>
</template>

<script setup></script>

<style></style>
