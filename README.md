# Tomos Solidity Contract

## Background

DDOS attacks have been on the rise for the last few years. A recent attack in October 2016 brought down major websites such as Github and Netflix through an affront on centralized DNS servers. 

The long term solution to DDOS attacks and to protect data availability is to move away from the modern decentralized methodology which has central points of failure and towards distributed solutions. Our contribution to the solution is our library Tomos which allows database interaction with the secure distributed network, Ethereum. With Tomos’ distribution, database access is available, even during high network stress.

## How it works 

Tomos is an Ethereum smart contract that you can include in your DApp (distributed application). By including Tomos, fully queryable databases are deployed to the Ethereum network. To access and update these databases simple RPC calls can be made to the contract.

Tomos can be used in any of your DApps to replace a traditional backend database. With just a few lines of code deploy the contract once from any of your applications and reference your database by ID to access your data. Try our simple example DApp below.

## Getting Started for Experienced Developers
* Go to Truffle and follow the instructions to deploy a simple DApp.
* Add the Tomos contract to your DApp.
* Reference Tomos functions on the client-side and enjoy!

## Getting Started for Beginners
Tomos's contract works as all typical Ethereum smart contracts do, but if you're getting started the easiest way is to use Truffle with TestRPC. Here are the steps to follow:
* Install Truffle ( http://truffleframework.com/ )
  * npm install -g truffle
* Install TestRPC ( https://github.com/ethereumjs/testrpc )
  * npm install -g ethereumjs-testrpc
* Create and Deploy Tomos contract
  * Initiate a new Truffle project ( http://truffleframework.com/docs/getting_started/project )
    * mkdir myproject
    * cd myproject
    * truffle init
  * Download Tomos
  * Include Tomos in Truffle contract directory
  * Edit migrations
    * In file myproject -> migrations -> 2_deploy_contracts.js
    * Replace test contracts with the following code:
      * module.exports = function(deployer) {
        deployer.deploy(Migrations);
      };
  * Compile all contracts
    * truffle compile
  * Start the TestRPC server
    * In the command line type "testrpc"
  * Deploy contracts to TestRPC
    * Type "truffle migrate" in the console
* Create and Build Client-Side DApp
  * Go to app -> javascripts -> app.js
  * Add in any Tomos functionality using Truffle's interface and Tomos' API
  * Build the DApp
    * Type "truffle build" in the console
  * Open the index.html file in your browser and enjoy Tomos!

## Tomos API Reference
* Tomos.createTable(bytes32 tableName, bytes32[] schema, bytes32[] dataTypes)
  * Create a new table within the database.
   * @param tableName Name of new table.
   * @param schema Definition of table schema.
   * @param dataTypes Definition of schema data types.
* Tomos.readTable(bytes32 tableName)
  * Read entire contents of table.
   * @param tableName Name of new table.
   * @return Flattened table contents.
* Tomos.getTableNames()
  * Get table names.
   * @return Table names.
* Tomos.createRow (bytes32 tableName, bytes32[] newRow)
  * Create a new row in a table.
   * @param tableName Name of table to create row.
   * @param newRow Definitions of new row data.
* Tomos.getTblWidth (bytes32 tableName)
  * Get width of a table.
   * @param tableName Name of desired table.
   * @return Width of table.
* Tomos.updateTable (bytes32 tableName, bytes32 searchColName, bytes32 searchVal, bytes32 colName, bytes32 value)
  * Search through matched records and update a field.
   * @param tableName Name of desired table.
   * @param searchColName Search column name.
   * @param searchVal Search value.
   * @param colName Column name to update.
   * @param value Value to update field.
* Tomos.removeRow(bytes32 tableName, bytes32 searchColName, bytes32 searchVal)
  * Delete a table row via matched column name and value.
   * @param tableName Name of desired table.
   * @param searchColName Search column name.
   * @param searchVal Search value.
* Tomos.removeRowHelper(bytes32 tableName, uint index)  returns(uint[])
  * Helper function called by removeRow function that deletes a specific row
   * @param tableName Name of desired table.
   * @param index Row to delete.
* Tomos.searchTable(bytes32 tableName, bytes32 colName, bytes32 value) returns(bytes32[])
  * Query data by row and value in table
   * @param tableName Name of desired table.
   * @param colName Column to search.
   * @param value Value to match.
   * @return Matched rows.
   
## Example App
We have a simple example DApp to get you started using Truffle and the Web3.js library.