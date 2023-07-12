<script lang="ts">
  let maxError: number = 40
  let virtualMaxWarning: number = 888
  let maxWarning: number = 30
  let virtualMaxOk : number = 888
  let virtualMinOk : number = 888
  let minWarning: number = 0
  let virtualMinWarning: number = 888
  let minError: number = -10
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
<p>
  Zakresy ostrzeżeń w formacie alertCondition[:warningConditon] (np. [-10]40:[0]30 )
</p>
<table>
  <tr>
    <td>ERROR</td>
    <td><input value="-∞" class="lock"  readonly/><br><input bind:value={maxError} /></td>
  </tr>
  <tr>
    <td>WARNING</td>
    <td><input bind:value={virtualMaxWarning}  class="lock"/><br><input bind:value={maxWarning} /></td>
  </tr>
  <tr>
    <td>OK</td>
    <td>
      <input bind:value={virtualMaxOk} class="lock"  />
      <br>
      <input bind:value={virtualMinOk} class="lock"  />
    </td>

    <!-- <td><input bind:value={minError} /></td> -->
  </tr>
  <tr>
    <td>WARNING</td>
    <td><input bind:value={minWarning} /><br><input bind:value={virtualMinWarning}  class="lock"/></td>
  </tr>
  <tr>
    <td>ERROR</td>
    <td><input bind:value={minError} /><br>
      <input value="∞" class="lock" readonly/></td>
  </tr>
</table>