# CAMPOS_IncomeTaxCalculator
<!DOCTYPE html>
<html>
  <body>
    <h1>Income Tax Calculator</h1><br>
    <label>Taxable Income: </label>
    <input type="number" id="ti" onkeyup="computeTax()">
    <br><br>
    <label>Tax Payable: </label>
    <input type="number" id="incometax" readonly>
    <link rel="stylesheet" href="IncomeTaxCalculator.css">
  </body> 

  <script>
    function computeTax() {
      let ti, basictax, brackettax, totaltax;

      ti = document.getElementById("ti").value * 1;

      if (ti < 250000) {
        basictax = 0;
        brackettax = 0;
      } else if (ti >= 250000 && ti < 400000) {
        basictax = 0;
        brackettax = 0.2 * (ti - 250000);
      } else if (ti >= 400000 && ti < 800000) {
        basictax = 30000;
        brackettax = 0.25 * (ti - 400000);
      } else if (ti >= 800000 && ti < 2000000) {
        basictax = 130000;
        brackettax = 0.3 * (ti - 800000);
      } else if (ti >= 2000000 && ti < 8000000) {
        basictax = 490000;
        brackettax = 0.32 * (ti - 2000000);
      } else {
        basictax = 2410000;
        brackettax = 0.35 * (ti - 8000000);
      }

      totaltax = basictax + brackettax;
      document.getElementById("incometax").value = totaltax.toFixed(2);
    }
  </script>
</html>