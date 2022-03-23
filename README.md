# smarter-netsuite
A collection of useful SuiteScripts and tools for NetSuite ERP.

## Useful Formulas in NetSuite Saved Searches
### Show a Customer/Vendor Name in a single column when A/P, A/R, and Journals are present in search results:
Use formula `COALESCE({name}, {vendor.entityid})`
