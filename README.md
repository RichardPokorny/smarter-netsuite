# smarter-netsuite
A collection of useful SuiteScripts and tools for NetSuite ERP.

## Useful Formulas in NetSuite Saved Searches
### Show a Customer/Vendor Name in a single column when A/P, A/R, and Journals are present in search results:
Use formula `COALESCE({name}, {vendor.entityid})`

### Link to a transaction's custom field:
`'<a href="https://4785302.app.netsuite.com/app/accounting/transactions/vendbill.nl?id='%7C%7C{custbody_eg_duplic_bill_tran.id}%7C%7C'"target="_blank">'||{custbody_eg_duplic_bill_tran}||'</a>'`
