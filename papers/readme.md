
## Statisticum: Data Statistics Management in SAP HANA 
Anisoara Nica, Reza Sherkat, Mihnea Andrei, Xun Cheng  
Martin Heidel, Christian Bensberg, Heiko Gerwens  
SAP SE  
http://www.vldb.org/pvldb/vol10/p1658-nica.pdf

**ABSTRACT**  
We introduce a new concept of leveraging traditional data statistics as dynamic data integrity constraints. These data statistics produce transient database constraints, which are valid as long as they can be proven to be consistent with the current data. We denote this type of data statistics by constraint data statistics, their properties needed for consistency checking by consistency metadata, and their implied integrity constraints by implied data statistics constraints (implied constraints for short). Implied constraints are valid integrity constraints which are powerful query optimization tools employed, just as traditional database constraints, in semantic query transformation (aka query reformulation), partition pruning, runtime optimization, and semi-join reduction, to name a few.
