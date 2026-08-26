# SQL POSTGRES

##Updating payment records for specific users in PostgreSQL and displaying the updated transaction results.

**STEPS**
1-Query used to find user payments

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
2-Query used to update the payment

UPDATE payments
SET status = 'COMPLETED'
FROM users
WHERE payments.user_id = users.id
and users.username  = 'zo alfakar';
3-Verification query

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

--------------------------------------

