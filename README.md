# Wallet Management

Laravel 10 wallet-management system for Laragon and MySQL. It provides secure wallet transactions, account sign-in, role-based permissions, a left-side dashboard menu, and EGP formatting.

## Roles

- **Manager:** Full access, including staff accounts and maximum wallet limits.
- **Operations employee:** May view wallet balances and record received/transferred transactions.
- **Wallet employee:** Has operations access and can also create wallets.

## Start in Laragon

1. Extract this project to `C:\laragon\www\wallet-management`.
2. Start **Apache** and **MySQL** in Laragon.
3. Open **Menu → MySQL → Console** and run:

   ```sql
   CREATE DATABASE wallet_management CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
   ```

4. In a terminal opened in the project folder, run:

   ```powershell
   composer install
   php artisan key:generate
   php artisan migrate --seed
   ```

5. Open `http://wallet-management.test` (or start Laragon's auto virtual-host feature).

## First manager account

- Email: `admin@wallet.test`
- Password: `password`

Change this password immediately after your first sign-in by replacing it in the database or adding your own manager account. The manager can then create employee accounts from **Staff accounts**.

## Tests

```powershell
php artisan test
```

## Monthly limits and export

Outgoing transfers use each wallet's monthly transfer limit. The unused amount resets automatically at the first use or visit in a new month; for an unattended reset, keep php artisan schedule:work running in Laragon. Managers may adjust a wallet balance and its monthly remaining limit from **Wallets**. Any signed-in user can download the current month's transactions from **Transactions** as a CSV file.
