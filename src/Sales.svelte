<script>
  let title = "Svales";
  import Navbar from "./Navbar.svelte";

  let cities = ["Seattle", "Tokyo", "Dubai", "Lima", "Paris"];
  const hours = Array.from({ length: 14 }, (_, i) => i + 6);

  let cityName = "";
  let minCustomersPerHour = "";
  let maxCustomersPerHour = "";
  let avgCookiesPerCustomer = "";
  let finalTotal = ""

  let salesData = cities.map(city => ({
    name: city,
    sales: hours.map(_ => generateCookies(100, 100, 1)),
  }));

  let hourlyTotals = [];

  $: {
    hourlyTotals = hours.map((_, hourIndex) => totalSalesByHour(hourIndex));
  }
  finalTotal = grandTotal()

  function handleSubmit() {
    const newCitySales = hours.map(_ => generateCookies(minCustomersPerHour, maxCustomersPerHour, avgCookiesPerCustomer));
    salesData = [...salesData, { name: cityName, sales: newCitySales }];
    finalTotal = grandTotal();
    hourlyTotals = hours.map((_, hourIndex) => totalSalesByHour(hourIndex));

    cityName = "";
    minCustomersPerHour = "";
    maxCustomersPerHour = "";
    avgCookiesPerCustomer = "";
  }

  function generateCookies(min, max, avg) {
    const customers = Math.floor(Math.random() * (max - min + 1) + min);
    return Math.round(customers * avg);
  }

  function totalSales(sales) {
    return sales.reduce((sum, sale) => sum + sale, 0);
  }

  function totalSalesByHour(hourIndex) {
    return salesData.reduce((sum, cityData) => sum + cityData.sales[hourIndex], 0);
  }

  function grandTotal() {
    return salesData.reduce((sum, cityData) => sum + totalSales(cityData.sales), 0);
  }
</script>


<Navbar />
<h1>{title}</h1>

<style>
  h1 {
    font-size: 3rem;
    text-align: center;
    background-color: aquamarine;
    margin: 0 0 25px 0;
    padding: .5em;

  }

  table {
    width: 100%;
    border-collapse: collapse;
  }

  th,
  td {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: center;
    cursor: cell;
  }

  th:hover, td:hover {background-color: aquamarine;}

  th {
    background-color: #f2f2f2;
    font-weight: bold;
  }

  form {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1rem;
    margin-top: 2rem;
  }

  input {
    width: 100%;
    max-width: 300px;
  }

  .submit-button {
    background-color: cadetblue;
    cursor: pointer;
    padding: .25em 1em
  }
</style>


<table>
  <thead>
    <tr>
      <th>City</th>
      {#each hours as hour}
        <th>{hour}:00</th>
      {/each}
      <th>Total</th>
    </tr>
  </thead>
  <tbody>
    {#each salesData as cityData}
      <tr>
        <td>{cityData.name}</td>
        {#each cityData.sales as sale}
          <td>{sale}</td>
        {/each}
        <td>{totalSales(cityData.sales)}</td>
      </tr>
    {/each}
  </tbody>
  <tfoot>
    <tr>
      <th>Total</th>
      {#each hours as hour, i}
        <td>{hourlyTotals[i]}</td>
      {/each}
      <td>{finalTotal}</td>
    </tr>
  </tfoot>
</table>

<form on:submit|preventDefault={handleSubmit}>
  <input type="text" placeholder="City Name" bind:value={cityName} required />
  <input type="number" placeholder="Min Customers Per Hour" bind:value={minCustomersPerHour} required />
  <input type="number" placeholder="Max Customers Per Hour" bind:value={maxCustomersPerHour} required />
  <input type="number" placeholder="Avg Cookies Per Customer" bind:value={avgCookiesPerCustomer} required />
  <button type="submit" class='submit-button'>Add City</button>
</form>
