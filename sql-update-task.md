# PostgreSQL


## (1) Managing Order Status Updates, Item Verifications, and Safe Transactions in PostgreSQL.

**STEPS:**

### 1.Query used to find pending payments for the user.

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
WHERE orders.status = 'pending'
and users.username = 'yasser';

```

### 2.Query used to update the payment status to completed.

```
UPDATE orders
SET status = 'COMPLETED'
FROM users
WHERE orders.user_id = users.id
and users.username  = 'yasser';

```

### 3.Query used to ensure only the selected pending orders were updated.

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
WHERE orders.status != 'pending';

```

### 4.Query used to verify the final status of all user orders.

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
WHERE users.username = 'yasser';

```

### 5.Query used to check related order items for the updated order.

```
select 
     orders.id,
     orders.product,
     order_items.quantity
FROM orders
JOIN order_items
    ON orders.id = order_items.id
WHERE orders.product = 'iPad';

```

### 6.Structure used to safely execute and rollback the update transaction.

```

BEGIN;

UPDATE orders
SET status = 'pending'
FROM users
WHERE orders.user_id = users.id
and users.username  = 'yasser';
 
select 
     orders.id,
     users.username,
     orders.product,
     orders.amount,
     orders.status,
     orders.created_at
FROM orders
JOIN users
    ON orders.user_id = users.id
WHERE orders.status = 'pending';

ROLLBACK;

```
