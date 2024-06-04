# Currently (Normal Flow):
- Expenses are added in any currency
- Converted at point of creation to Local Currency
- On Customers Side
	- Displayed to customer
		- Expense : Billing
		- At the point creation
		- DOESNT include FX Fee
- Approved at that rate
- Goes into Payroll
- Snapshot Created -> Exchange Rates Stored at that point
- What goes into the calculator
	- Saved Local Currency (That it was at the time of logging the Expense)
- Invoice Calculations:
	- Converted from LOCAL to BILLING using Run-Specific-Exchange- List

---
## -> Local Salary Payment
Billing Currency: EUR
Local Currency: NGN

Expense Logged as 100 USD
Displayed to Employer as 101 EUR
Converted to Local -> 10,000 NGN

Enters Calc as 10,000 NGN
- in Payroll Provider Report

At Invoicing:
-> 10,000 NGN : EUR ~ 102 EUR (*Run-Specific-Exchange- Rate*)
-> +2.5%

---

# Currently (For SPDC):
- Expenses are added in any currency
- Converted at point of creation to Local Currency
- On Customers Side
	- Displayed to customer
		- Expense : Billing
		- At the point creation
		- DOESNT include FX Fee
- Approved at that rate
- Snapshot Created -> Exchange Rates Stored at that point
- What goes into the calculator
	- Saved Local Currency (That it was at the time of logging the Expense)
	- in Calculation Results:
		- For FC Payment:
			- converted to SP currency at rate defined for that cycle
		- For Pegged (Direct)
			- uses saved local currency (not converted) (rate from creation date)
- Invoice Calculations:
	- Converted from LOCAL to BILLING using Run-Specific-Exchange- List
---
## -> Employee Actually Paid in USD
SP Currency: USD
Billing Currency: EUR
Local Currency: NGN

Expense Logged as 100 USD
Converted to Local -> 10,000 NGN

Enters Calc as 10,000 NGN
Converted back to USD at  *Run-Specific-Exchange- Rate*
-> 105 USD
- in Payroll Provider Report

At Invoicing:
-> 105 USD : EUR ~ 102 EUR

## -> Direct Pegged
SP Currency: USD
Billing Currency: EUR
Local Currency: NGN

Expense Logged as 100 USD
Converted to Local -> 10,000 NGN

Enters Calc as 10,000 NGN
- in Payroll Provider Report

At Invoicing:
-> 10,000 NGN : EUR ~ 102 EUR (*Run-Specific-Exchange- Rate*)
-> +2.5%

--- 


Normal:
-> Fixed Rate at time of logging (Expense:Local)
-> Convert from Local -> Billing based on Cycle Rate

For SPDC: 
Same, Fix rate at time of billing
-> (Expense:SP:Local)
-> Must go into calc as SP
-> Recalculated in Local (Taxes added based on this local amount)
-> Converted from Local -> Billing

IF Expense Currency = SP/Local currency = Billing
-> "Why did I pay more for this expense?"
--> "Billing conversion calculation is based on an aggregated exchange rate fixed on the 5th of each month at Playroll Payroll Cutoff on Payroll"

---
