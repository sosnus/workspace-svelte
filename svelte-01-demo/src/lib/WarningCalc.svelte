<script lang="ts">
  let minError: number = 42
  let minWarning: number = 0
  let maxWarning: number = 0
  let maxError: number = 0
  const increment = () => {
    // count += 1
  }
  
</script>
<style>
  .lock {
color: gray;
  /* padding-left: 25px; */
  /* background: url("https://static.thenounproject.com/png/101791-200.png") no-repeat left; */
  /* background-size: 20px; */
}
</style>

<!-- <button on:click={increment}>
  count is {minError}
</button> -->
<table>
  <tr>
    <td>ERROR</td>
    <td><input value="-∞" class="lock"  readonly/><br><input bind:value={minError} /></td>
  </tr>
  <tr>
    <td>WARNING</td>
    <td><input bind:value={minError} /></td>
  </tr>
  <tr>
    <td>OK</td>
    <td>
      <input value="-∞" class="lock"  readonly/><br>
      <input bind:value={minError} class="lock"  />
    </td>

    <!-- <td><input bind:value={minError} /></td> -->
  </tr>
  <tr>
    <td>WARNING</td>
    <td><input bind:value={maxWarning} /></td>
  </tr>
  <tr>
    <td>ERROR</td>
    <td><input bind:value={maxError} /><br>
      <input value="∞" class="lock" readonly/></td>
  </tr>
</table>