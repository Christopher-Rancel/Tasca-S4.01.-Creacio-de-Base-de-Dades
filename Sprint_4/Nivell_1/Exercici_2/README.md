# Nivell 1 - Exercici 2

## Enunciat

Mostra la mitjana d'amount per IBAN de les targetes de crèdit a la companyia Donec Ltd, utilitza almenys 2 taules.

---

## Descripció

En aquest exercici es calcula la mitjana de l'import (`amount`) de les transaccions associades a cada IBAN de targeta de crèdit per a una companyia concreta.

Per fer-ho, es relacionen les taules `transaction`, `credit_card` i `company` mitjançant operacions `JOIN`, filtrant per la companyia `"Donec Ltd"` i agrupant per IBAN.

---

## Resolució

```sql
USE transactions;

SELECT c.iban, AVG(t.amount) AS avg_amount
FROM transaction t
JOIN credit_card c ON t.card_id = c.id
JOIN company co ON t.business_id = co.company_id
WHERE co.company_name = 'Donec Ltd'
GROUP BY c.iban;
```

---

## Conclusió

Aquesta consulta permet obtenir la mitjana d'import de les transaccions per cada targeta de crèdit associada a una empresa concreta, facilitant l'anàlisi del comportament de compra.
