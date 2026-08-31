# PostgreSQL



## Updating payment records for specific users in PostgreSQL and displaying the updated transaction results.

**STEPS:**

### 1.Query used to find user payments.

```

SELECT
    users.username,
    payments.id,
    payments.amount,
    payments.status,
    payments.created_at
FROM payments
JOIN users
    ON payments.user_id = users.id
WHERE users.username = 'zo alfakar';

```

### 2.Query used to update the payment.

```

UPDATE payments
SET status = 'COMPLETED'
FROM users
WHERE payments.user_id = users.id
and users.username  = 'zo alfakar';

```

### 3.Verification query.

```

SELECT
    users.username,
    payments.id,
    payments.amount,
    payments.status,
    payments.created_at
FROM payments
JOIN users
    ON payments.user_id = users.id
WHERE users.username = 'zo alfakar';
=======
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
>>>>>> main

```

