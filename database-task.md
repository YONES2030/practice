# PostgreSQL

## SELECT query that returns all cancelled orders using the users and orders tables.

### conditions:
The result should include:

* order ID
* username
* product
* amount
* status
* creation date

```

SELECT 
     orders.id,
     users.username,
     orders.product,
     orders.amount,
     orders.status,
     orders.created_at
FROM orders
JOIN users
    ON orders.user_id = users.id
WHERE orders.status = 'cancelled';

```

