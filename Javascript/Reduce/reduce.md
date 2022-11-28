# Reduce

Exemplos de uso do metodo Reduce

### Realizando somatório de transações bancárias

```js
const summary = transactions.reduce(
  (acc, transaction) => {
    if (transaction.type === "deposit") {
      acc.deposits += transaction.amount;
      acc.total += transaction.amount;
    } else {
      acc.withdraws += transaction.amount;
      acc.total -= transaction.amount;
    }

    return acc;
  },
  {
    deposits: 0,
    withdraws: 0,
    total: 0,
  }
);
```
