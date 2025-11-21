# **Cash-Flow Minimizer System**

This project implements a **Cash-Flow Minimization System** for settling transactions among multiple banks that support different payment modes. The goal is to **reduce the total number of money transfers** while ensuring that all debts are cleared using supported payment modes. A **World Bank** (supporting all modes) acts as an intermediary whenever two banks lack a common payment mode.


## **Problem Overview**

Given:

* A list of banks
* The payment modes each bank supports
* A list of directed transactions *(Debtor → Creditor → Amount)*
  The system first converts all transactions into **net amounts** for every bank:

```
netAmount = (total incoming payments) – (total outgoing payments)
```

* Positive net amount → **Creditor**
* Negative net amount → **Debtor**

The algorithm repeatedly matches:

1. **Maximum debtor**
2. **Maximum creditor**
3. Having at least one **shared payment mode**

The debtor pays the creditor using the smallest possible settlement amount.
If no shared mode exists, settlement is routed through the **World Bank**.

This process continues until all banks reach a net amount of zero.


## **Key Features**

* Minimizes number of transactions.
* Supports multiple payment modes.
* Handles cases where banks have **no shared modes** via an intermediary.
* Uses a **greedy settlement algorithm** based on creditor–debtor pairing.
* Conceptually representable as a **Max-Flow (Ford–Fulkerson) model**, but implemented using an efficient iterative approach.

## **Algorithm Flow** 

1. Read all banks and their supported payment modes.  
2. Read all transactions and build a directed graph.  
3. Compute net amounts for every bank.  
4. Repeat until all net amounts become zero:
   -  Find max debtor (min net value)  
   -  Find max creditor (max net value)  
   -  Check intersection of payment modes  
   -  If no common mode → route payment through World Bank  
   -  Transfer `min(abs(debtor), creditor)`  
   -  Update net balances  
5. Print minimized transactions.


## **How It Works**

1. Read bank names and their supported payment modes.
2. Read all input transactions into an adjacency matrix.
3. Compute net amounts for every bank.
4. Iteratively match max-creditor and max-debtor pairs with common payment modes.
5. Route unmatched pairs via the World Bank.
6. Print the final minimized settlement plan.

Thank You

