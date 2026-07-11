---
name: compounding-calculator-html
description: An interactive HTML-based skill to calculate compound interest instantly
version: 1.0.0
author: AI Developer
---

# Interactive Compounding Calculator

## Purpose

Financial assistant with interactive interface for compound interest calculations.

## Interactive Tool

```html
<div style="font-family: Arial, sans-serif; max-width: 400px; margin: 20px auto; padding: 20px; border: 1px solid #ccc; border-radius: 8px; background-color: #f9f9f9;">
    <h3 style="text-align: center; color: #333; margin-top: 0;">Compounding Calculator</h3>
    
    <label style="display:block; margin: 10px 0 5px;">Principal Amount:</label>
    <input type="number" id="principal" value="10000" style="width: 100%; padding: 8px; box-sizing: border-box; border: 1px solid #ccc; border-radius: 4px;">
    
    <label style="display:block; margin: 10px 0 5px;">Annual Rate (%):</label>
    <input type="number" id="rate" value="5" step="0.01" style="width: 100%; padding: 8px; box-sizing: border-box; border: 1px solid #ccc; border-radius: 4px;">
    
    <label style="display:block; margin: 10px 0 5px;">Time (Years):</label>
    <input type="number" id="years" value="10" style="width: 100%; padding: 8px; box-sizing: border-box; border: 1px solid #ccc; border-radius: 4px;">
    
    <label style="display:block; margin: 10px 0 5px;">Frequency:</label>
    <select id="frequency" style="width: 100%; padding: 8px; box-sizing: border-box; border: 1px solid #ccc; border-radius: 4px;">
        <option value="1">Annually</option>
        <option value="4">Quarterly</option>
        <option value="12">Monthly</option>
        <option value="365">Daily</option>
    </select>
    
    <button onclick="calc()" style="width: 100%; margin-top: 15px; padding: 10px; background-color: #007bff; color: white; border: none; border-radius: 4px; font-size: 16px; cursor: pointer;">Calculate</button>
    
    <div id="resultBox" style="display:none; margin-top: 15px; padding: 10px; background-color: #e9ecef; border-left: 4px solid #007bff;">
        <p><strong>Final Balance:</strong> <span id="finalBalance">$0.00</span></p>
        <p><strong>Total Interest:</strong> <span id="totalInterest">$0.00</span></p>
    </div>
</div>

<script>
function calc() {
    const P = parseFloat(document.getElementById('principal').value);
    const r = parseFloat(document.getElementById('rate').value) / 100;
    const t = parseFloat(document.getElementById('years').value);
    const n = parseInt(document.getElementById('frequency').value);
    
    if (isNaN(P) || isNaN(r) || isNaN(t)) {
        alert("Enter valid numbers");
        return;
    }
    
    const A = P * Math.pow((1 + (r / n)), (n * t));
    const interest = A - P;
    
    document.getElementById('finalBalance').innerText = '$' + A.toFixed(2);
    document.getElementById('totalInterest').innerText = '$' + interest.toFixed(2);
    document.getElementById('resultBox').style.display = 'block';
}
</script>
```

## Usage

1. Enter Principal Amount
2. Enter Annual Interest Rate
3. Enter Time in Years
4. Select Compounding Frequency
5. Click Calculate
