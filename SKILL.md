---
name: compounding-calculator-html
description: An interactive HTML-based skill to calculate compound interest instantly using input fields and a button.
version: 1.0.0
author: AI Developer
---

# Interactive Compounding Calculator

## Purpose
You are a financial assistant with an interactive interface. When users want to calculate compounding interest, display the HTML tool below so they can easily enter their values, press a button, and get instant results.

## Interactive Tool
Below is the interactive calculator component. You can render this directly to the user so they can input values and press the calculate button.

```html
<div style="font-family: Arial, sans-serif; max-width: 400px; margin: 20px auto; padding: 20px; border: 1px solid #ccc; border-radius: 8px; background-color: #f9f9f9;">
    <h3 style="text-align: center; color: #333; margin-top: 0;">Compounding Calculator</h3>
    
    <label style="display:block; margin: 10px 0 5px;">Principal Amount ($):</label>
    <input type="number" id="principal" value="10000" style="width: 100%; padding: 8px; box-sizing: border-box; border: 1px solid #ccc; border-radius: 4px;">
    
    <label style="display:block; margin: 10px 0 5px;">Annual Interest Rate (%):</label>
    <input type="number" id="rate" value="5" step="0.01" style="width: 100%; padding: 8px; box-sizing: border-box; border: 1px solid #ccc; border-radius: 4px;">
    
    <label style="display:block; margin: 10px 0 5px;">Time (Years):</label>
    <input type="number" id="years" value="10" style="width: 100%; padding: 8px; box-sizing: border-box; border: 1px solid #ccc; border-radius: 4px;">
    
    <label style="display:block; margin: 10px 0 5px;">Compounding Frequency:</label>
    <select id="frequency" style="width: 100%; padding: 8px; box-sizing: border-box; border: 1px solid #ccc; border-radius: 4px;">
        <option value="1">Annually (1/year)</option>
        <option value="4">Quarterly (4/year)</option>
        <option value="12">Monthly (12/year)</option>
        <option value="365">Daily (365/year)</option>
    </select>
    
    <button onclick="calculateCompounding()" style="width: 100%; margin-top: 15px; padding: 10px; background-color: #007bff; color: white; border: none; border-radius: 4px; font-size: 16px; cursor: pointer;">Calculate</button>
    
    <div id="resultBox" style="display:none; margin-top: 15px; padding: 10px; background-color: #e9ecef; border-left: 4px solid #007bff; border-radius: 4px;">
        <p style="margin: 5px 0;"><strong>Final Balance:</strong> <span id="finalBalance">$0.00</span></p>
        <p style="margin: 5px 0;"><strong>Total Interest Earned:</strong> <span id="totalInterest">$0.00</span></p>
    </div>
</div>

<script>
function calculateCompounding() {
    // Get values from input fields
    const P = parseFloat(document.getElementById('principal').value);
    const r = parseFloat(document.getElementById('rate').value) / 100;
    const t = parseFloat(document.getElementById('years').value);
    const n = parseInt(document.getElementById('frequency').value);
    
    if (isNaN(P) || isNaN(r) || isNaN(t)) {
        alert("Please enter valid numbers in all fields.");
        return;
    }
    
    // Compounding Formula: A = P * (1 + r/n)^(n*t)
    const A = P * Math.pow((1 + (r / n)), (n * t));
    const interest = A - P;
    
    // Display results formatted as currency
    document.getElementById('finalBalance').innerText = '$' + A.toFixed(2);
    document.getElementById('totalInterest').innerText = '$' + interest.toFixed(2);
    document.getElementById('resultBox').style.display = 'block';
}
</script>
```

## How to Use
1. Enter the **Principal Amount** (initial investment)
2. Enter the **Annual Interest Rate** (as a percentage)
3. Enter the **Time** in years
4. Select the **Compounding Frequency** (Annual, Quarterly, Monthly, or Daily)
5. Click **Calculate** to see your final balance and total interest earned
