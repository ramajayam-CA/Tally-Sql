# Tally-Sql
Tally Sql Query


https://help.tallysolutions.com/article/Tally.ERP9/Data_Management/DM_SQL_Query.htm

ou can use SQL query language in Tally.ERP 9 to retrieve information.

Introduction
The Calculator Area in Tally.ERP 9 can be used for processing SQL Queries .



Tally.ERP 9 has an in-built SQL processor that processes SQL Select statements on collections. The collections which are exposed to ODBC are available as tables to the external applications. By default, the methods at the first level of the collection are available for selection.

The general syntax to write an SQL Query in Tally.ERP 9 is:

SELECT [<Method Name/s> / <*>] FROM <Collection/Table> WHERE <Condition> ORDER BY <Method Name/s>

Note : SQL is not case sensitive. SELECT is the same as select.

For Example let’s write a simple SQL Query to retrieve the names of all the Ledgers:

SELECT $Name FROM Ledger



Here, $Name is the Method Name and Ledger is the Collection.

A Collection is where all the stored information is available. The collection Ledger will have all the information about all the ledgers in the company.

A method is where the particular information of a collection is stored. The method $Name is where the names of all the Ledgers are stored.

Note : The method names will always starts with a “ $ ”.

The result of the above SQL Query is the list if all the ledgers in the company and will be listed as shown:



Note : In a SQL Query the WHERE clause and ORDER BY keyword are optional. The WHERE clause is used to filter the search and the ORDER BY keyword is used to view the results in the desired order.

Examples of SQL Queries
SELECT Statement
1. To retrieve list of all the Collections which are exposed to ODBC

SELECT $Name FROM ODBCTables

2. To retrieve one method from a collection; say $Name method from Ledger collection

SELECT $Name FROM Ledger

3. To retrieve more than one method from a collection, separate the method names with a comma. For example, to retrieve $Name and $ClosingBalance of Ledger collection

SELECT $Name, $ClosingBalance FROM Ledger

4. To display all methods of a collection; for example, retrieve all the methods of Ledger collection. This SQL Query can be used to discover all the Methods available for a Collection.

SELECT * FROM Ledger

Note : “*” will retrieve all the methods of a collection

WHERE Clause
The WHERE clause is used to filter queries based on conditions using functions, mathematical/logical expressions, and patterns/strings.

1. Retrieve the names of the ledgers with only debit closing balance using Functions

SELECT $Name FROM Ledger WHERE $$IsDr: $ClosingBalance

Note : to get Credit Closing Balance use the function “NOT $$IsDr”.

2. Retrieve the names of the ledgers whose closing balance is between 10000 and 11000

SELECT $Name FROM Ledger WHERE $ClosingBalance BETWEEN 10000 AND 11000

3. Retrieve the names of the ledgers which have the word “sales” in their name

SELECT $Name FROM ledger WHERE $name LIKE '%sales%'

Note : The "%" sign can be used to define wildcards (missing letters in the pattern) both before and after the pattern.

With the WHERE clause, the following Mathematical operators can also be used:

Operator

Description

=

Equal to

< > or !=

Not equal to

>

Greater than

<

Less than

>=

Greater than or equal to

<=

Less than or equal to

ORDER BY Keyword
To sort the result of the query the ORDER BY keyword is used. The ORDER BY keyword sorts the result of the query in ascending order by default. To sort the results in descending order the DESC keyword is used

1. For example, to display the names and debit closing balances of all Ledger objects sorted in descending order of closing balances

SELECT $Name, $ClosingBalance FROM Ledger WHERE $$IsDr: $ClosingBalance ORDER BY $ClosingBalance DESC


SELECT $Key, $MasterId, $AlterID, $VoucherNumber, $Date, $VoucherTypeName, $_Narration, $Reference, $ReferenceDate, $IsDeemedPositive, $NatureOfVoucher, $HasCashFlow, $EnteredBy, $AlteredBy, $AlteredOn, $SUpdatedDate, $SUpdatedTime, $LedgerName, $Amount, $DrAmount, $CrAmount, $Ledger_Parent, $Ledger_PrimaryGroup, $Party_LedgerName, $PARTY_GST_number, $Ledger_Master_GST_Number, $LedgerMasterGSTINGSTINtype, $HasBankEntry, $RComp_Name, $Year_Selected_from, $Year_Selected_to, $Company_number, $Led_Master_id, $Led_Alter_Id, $Led_IS_Revenue, $Path_of_the_CurrentCompany FROM A_Sirc_Vourcher7_1




SELECT $Name, $_PrimaryGroup, $Parent, $OpeningBalance, $ClosingBalance, $_PrevYearBalance, $IsRevenue, $PartyGSTIN, $MasterId, $alteridd, $RComp_Name, $Year_Selected_from, $Year_Selected_to, $Company_number, $Path FROM A_Sirc_Leder_Detailed_7_1




