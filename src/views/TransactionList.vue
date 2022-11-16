<template>
  <h1>Transactions (3)</h1>
  <div>
    <div>
      <button>
        <p>Add Income</p>
      </button>
      <button>
        <p>Add Expense</p>
      </button>

      <button>
        <p>View Debts</p>
      </button>

      <input type="text" placeholder="Search transactions" />

      <button>
        <p>Filter</p>
      </button>
    </div>

    <div>
      <table>
        <thead>
          <tr>
            <th></th>
            <th>
              <span>
                <p>Date</p>
              </span>
            </th>
            <th>
              <span>
                <p>Customer Name</p>
              </span>
            </th>
            <th>
              <span>
                <p>Amount</p>
              </span>
            </th>
            <th>
              <span>
                <p>Payment Method</p>
              </span>
            </th>
            <th>
              <span>
                <p>Products</p>
              </span>
            </th>
            <th>
              <span>
                <p>Quantity</p>
              </span>
            </th>
          </tr>
        </thead>

        <tbody>
          <tr>
            <td></td>
            <td>
              <span>
                <p>15 November 2022</p>
              </span>
            </td>
            <td>
              <span>
                <p>₦12,000.00</p>
              </span>
            </td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
          </tr>

          <tr>
            <td>
              <input type="checkbox" />
            </td>
            <td>
              <span> 15-Nov-22 </span>
              <p>12:41 PM</p>
            </td>
            <td>
              <div>
                <span> John Doe </span>

                <span> johndoe@mail.com </span>
              </div>
            </td>
            <td>
              <p>₦1,500.00</p>
            </td>
            <td>Bank Transfer</td>
            <td>
              <p>Product1, Product2</p>
            </td>
            <td>2</td>
          </tr>
          <tr>
            <td>
              <input type="checkbox" />
            </td>
            <td>
              <span> 15-Nov-22 </span>
              <p>11:30 AM</p>
            </td>
            <td>
              <div>
                <div>
                  <span> Customer Two </span>

                  <span> customer@mail.com </span>
                </div>

                <div>
                  <p>unpaid</p>
                </div>
              </div>
            </td>
            <td>
              <p>₦3,000.00</p>
            </td>
            <td></td>
            <td>
              <p>Product1, Product2, Product3</p>
            </td>
            <td>3</td>
          </tr>
          <tr>
            <td>
              <input type="checkbox" />
            </td>
            <td>
              <span> 15-Nov-22 </span>
              <p>9:41 AM</p>
            </td>
            <td>
              <div>
                <span> Customer One </span>

                <span> customerone@mail.com </span>
              </div>
            </td>
            <td>
              <p>
                <span> ₦2,700.00</span>
                <span> of ₦7,000.00 </span>
              </p>
            </td>
            <td>Cash</td>
            <td>
              <p>Product10</p>
            </td>
            <td>1</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup></script>

<style scoped></style>
