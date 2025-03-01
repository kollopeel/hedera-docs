# Queries

Queries are requests that do not require network consensus. Queries are processed only by the single node the request is sent to. Below is a list of network queries by service.

| Cryptocurrency Accounts                                      | Consensus                                           | Tokens                                                   | File Service                                           | Smart Contracts                                                                                                                | Schedule Service                                               |
| ------------------------------------------------------------ | --------------------------------------------------- | -------------------------------------------------------- | ------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------- |
| [AccountBalanceQuery](cryptocurrency/get-account-balance.md) | [TopicInfoQuery](consensus/get-topic-info.md)       | [TokenBalanceQuery](tokens/get-account-token-balance.md) | [FileContentsQuery](file-storage/get-file-contents.md) | [ContractCallQuery](smart-contracts/call-a-smart-contract-function-1.md)                                                       | [ScheduleInfoQuery](schedule-transaction/get-schedule-info.md) |
| [AccountInfoQuery](cryptocurrency/get-account-info.md)       | [TopicMessageQuery](consensus/get-topic-message.md) | [TokenInfoQuery](tokens/get-token-info.md)               | [FileInfoQuery](file-storage/get-file-info.md)         | [ContractByteCodeQuery](smart-contracts/get-smart-contract-bytecode.md)                                                        |                                                                |

## Get Query Cost

A query that returns the cost of a query prior to submitting the query to the network node for processing. If the cost of the query is greater than the default max query payment (1 HBAR) you can use `setMaxQueryPayment(<hbar>)` to change the default.

| Method                       | Type             | Description                                                                                                   |
| ---------------------------- | ---------------- | ------------------------------------------------------------------------------------------------------------- |
| `getCost(<client>)`          | Client           | Get the cost of the query in HBAR                                                                             |
| `getCost(<client, timeout>)` | Client, Duration | The max length of time the SDK will attempt to retry in the event of repeated busy responses from the node(s) |
| `getCostAsync(<client>)`     | Client           | Get the cost of a query asynchronously                                                                        |

{% tabs %}
{% tab title="Java" %}
```java
//Create the query request
AccountBalanceQuery query = new AccountBalanceQuery()
     .setAccountId(accountId);

//Get the cost of the query
Hbar queryCost = query.getCost(client);

System.out.println("The account balance query cost is " +queryCost);

//v2.0.0
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Create the query request
const query = new AccountBalanceQuery()
     .setAccountId(accountId);

//Get the cost of the query
const queryCost = await query.getCost(client);

console.log("The account balance query cost is " +queryCost);

//v2.0.0
```
{% endtab %}

{% tab title="Go" %}
```java
//Create the query request
query := hedera.NewAccountBalanceQuery().
     SetAccountID(newAccountId)

//Get the cost of the query
cost, err := query.GetCost(client)

if err != nil {
		panic(err)
}

fmt.Printf("The account balance query cost is: %v\n ", cost.String())

//v2.0.0
```
{% endtab %}
{% endtabs %}
