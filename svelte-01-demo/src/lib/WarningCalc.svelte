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
    console.log(virtualMinWarning)
    command = "<" + minError + ">" + maxError + ":" + "<" + minWarning + ">" + maxWarning;

    // console.log("Change!");
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

<!-- 
  TODO:
Wersja wielojęzykowa
Ukrycie warna (opcjonalnie)
dodanie nazwy zmiennej na którą algorytm ma reagować (np @temperature)
walidacja
kropka-przecinek
co gdy user wpisze "," albo stringa?
zmiana error, warning na alert,warning
zaokr. do 3 msc po przecinku
dodać tester!
sprawdzać typowanie? - jak ominąć stringi?
-->
<h3>Kreator zakresów ostrzeżeń</h3>
<p>
  Kreator ma za zadanie ułatwić stworzenie odpowiedniego stringa którego celem jest zmiana koloru komunikatu w zależności od wartości. Wystarczy w edytowalen pola wpisać zakresy, a na dole zostanie wygenerowany gotowy zakres ostrzeżeń, który należy wkleić w pole "Zakresy ostrzeżeń"
</p>
<p>
  Zakresy ostrzeżeń w formacie alertCondition[:warningConditon] (np. <b>{info}</b> )
</p>
<table>
  <tr style="background-color:#dc3545">
    <td>ALERT</td>
    <td><input value="∞" class="lock"  readonly/><br><input type="number" bind:value={maxError} on:change={recalc} on:keypress={recalc} on:change={recalc} /></td>
  </tr>
  <tr style="background-color:#ffc107">
    <td>WARNING</td>
    <td><input type="number" bind:value={virtualMaxWarning} class="lock" readonly/><br><input type="number"  on:change={recalc} on:keypress={recalc} on:change={recalc} bind:value={maxWarning} /></td>
  </tr>
  <tr style="background-color:#007bff">
    <td>OK</td>
    <td>
      <input type="number" bind:value={virtualMaxOk} class="lock" readonly  />
      <br>
      <input type="number" bind:value={virtualMinOk} class="lock" readonly  />
    </td>
  </tr>
  <tr style="background-color:#ffc107">
    <td>WARNING</td>
    <td><input type="number" bind:value={minWarning} on:change={recalc} on:keypress={recalc} on:change={recalc} /><br><input type="number" bind:value={virtualMinWarning}  class="lock"/></td>
  </tr>
  <tr style="background-color:#dc3545">
    <td>ALERT</td>
    <td><input type="number" bind:value={minError}  on:change={recalc} on:keypress={recalc} on:change={recalc}/><br>
      <input value="-∞" class="lock" readonly/></td>
  </tr>
</table>
COMMAND: <br>
<input  bind:value={command} class="lock" readonly />
<p>
  Skopiuj powyższa linijkę z pola tekstowego i wklej w pole "Zakresy ostrzeżeń" w platformie.
</p>