# Playroll Invoicing Overview:

1. **Monthly Invoices**
	-  Generated on a Xero report that we provide to finance on the 10th of the month
		- Generated based on the calculation results from any payroll inputs for an employee (frozen at the time of the payroll cutoff)
		- The exchange rates used here are stored at the time of cutoff and used throughout the month
			- lets call this the #cycleExchangeRates
		-  Exchange Rates can be found [here](Expenses.md)
2. **Out of Cycle Invoices/Credit Notes**
	- Generated based on the delta between the monthly invoice and the newly generated invoice for a specific customer
		- Changes are made by updating the snapshot, re-runing calculations and then synchronising those changes with the live DB
		- The #cycleExchangeRates are maintained during this invoice generation
		- Future: Only if Customer requested it do we issue a new invoice 
			- Otherwise -> Part of following months Variance Upload
3. **Deposits:**
	- Every time and addendum is signed a deposit calculation is generated for the employee's starting months costs (always excluding apportionment if it were to apply (i.e when start date is not the first working day of the month))
	- Deposit Calculations are added to the employee's profile on the admin panel
		- These are then verified by the ESM (To make sure the employee isn't a Visa employee, sense check the total ctc etc)
		- A status is changed on monday.com to send this to finance who will then generate the PDF in Xero and send to the customer
		- Finance should then be updating the status once paid (On our roadmap is a consideration to automate the generation of the invoices in Xero as well as align the statuses on the admin panel and Xero)
![Alt text](/Expenses%20Flow.png "Title")
4. **Deposit Refunds:**
	-  No Product Involvement ➜ Fully between Ops and Finance
		- ![[image (17).png]]
	- See plans as a possible route to automate :IbReturnUp:
5. **Manual Adjustments**
	- Service Fees:
		- Legal Fees
		- Visa Applications
			- Invoiced Separately because we on-charge them
	- Material Salary Adjustments (Positive) that come through AFTER out of cycles


#### Priority
##### ➜ to Automate/Resolve Issues:
1. Monthly Invoices/OOCs
	1. Create Invoices in Xero from Platform (Bypass Xero Bulk Upload Report)
    1. **Sync Invoice Statuses**
	2. Automated Delta Calculation based on whats on platform
		1. Pick up OOC client request
			1. Either Delta Invoice 
			   OR
			2. Push to next month
- Deposits
	- _See above_ ☝️
- Deposit Refunds
	- _See above_ ☝️
	-   Automate Early Termination Fees Flag **(Defined per customer by legal)**
- Manual Adjustments
	- (**-> Check this board**)
	- Fix Company IDs on CS/ES board
