<script lang="ts">
  let maxError: number = 40
  let virtualMaxWarning: number = 888
  let maxWarning: number = 30
  let virtualMaxOk : number = 888
  let virtualMinOk : number = 888
  let minWarning: number = 0
  let virtualMinWarning: number = 888
  let minError: number = -10
  let command : string = "to be calc"
  let info : string = "<-10>40:<0>30"

  
  const recalc = () => {
    // count += 1
    virtualMaxWarning = maxError - 0.001;
    virtualMaxOk = maxWarning - 0.001;
    virtualMinOk = minWarning + 0.001;
    virtualMinWarning = minError + 0.001;
    command = "<" + minError + ">" + maxError + ":" + "<" + minWarning + ">" + maxWarning;

    console.log("Change!");
  }
  recalc(); // first run
  
</script>
<style>
  .lock {
color: gray;
/* font-weight: bold; */
}
</style>

<!--
007bff - OK
ffc107 - WARNIG
dc3545 - ERROR
-->

<!-- 
  :root {
  --blue: #007bff;
  --indigo: #6610f2;
  --purple: #6f42c1;
  --pink: #e83e8c;
  --red: #dc3545;
  --orange: #fd7e14;
  --yellow: #ffc107;
}
-->

<p>
  Zakresy ostrzeżeń w formacie alertCondition[:warningConditon] (np. <b>{info}</b> )
</p>
<table>
  <tr style="background-color:#dc3545">
    <td>ERROR</td>
    <td><input value="∞" class="lock"  readonly/><br><input bind:value={maxError} /></td>
  </tr>
  <tr style="background-color:#ffc107">
    <td>WARNING</td>
    <td><input bind:value={virtualMaxWarning} class="lock"/><br><input  on:change={recalc}  bind:value={maxWarning} /></td>
  </tr>
  <tr style="background-color:#007bff">
    <td>OK</td>
    <td>
      <input bind:value={virtualMaxOk} class="lock"  />
      <br>
      <input bind:value={virtualMinOk} class="lock"  />
    </td>

    <!-- <td><input bind:value={minError} /></td> -->
  </tr>
  <tr style="background-color:#ffc107">
    <td>WARNING</td>
    <td><input bind:value={minWarning} /><br><input bind:value={virtualMinWarning}  class="lock"/></td>
  </tr>
  <tr style="background-color:#dc3545">
    <td>ERROR</td>
    <td><input bind:value={minError} /><br>
      <input value="-∞" class="lock" readonly/></td>
  </tr>
</table>
COMMAND: <br>
<input bind:value={command} class="lock"  />