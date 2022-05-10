# smarter-netsuite
A collection of useful SuiteScripts and tools for NetSuite ERP.

## Useful Formulas in NetSuite Saved Searches
### Show a Customer/Vendor Name in a single column when A/P, A/R, and Journals are present in search results:
Use formula `COALESCE({name}, {vendor.entityid})`

### Link to a transaction using a custom body field
`'<a href="https://XXX.app.netsuite.com/app/accounting/transactions/vendbill.nl?id='|||{custbody_YYY}||'"target="_blank">'||{custbody_YYY}||'</a>'`
