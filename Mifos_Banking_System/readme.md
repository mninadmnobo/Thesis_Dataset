# Mifos Functional Testing Dataset

## About Mifos

Mifos (Microfinance Open Source) is a comprehensive core banking and microfinance platform built on Apache Fineract. It provides financial institutions — including microfinance organizations, credit unions, cooperatives, and small banks — with a complete suite for managing clients, loans, savings, shares, accounting, and organizational operations. The platform supports multi-tenancy, maker-checker workflows, granular role-based access control, and configurable products. The web interface (OpenMF Community App) is an Angular-based single-page application communicating with the Fineract REST API backend.

## Requirements

- Docker
- Docker Compose

## Start the system

Run:

docker compose up -d

## Access the application

http://localhost:4200

## Credentials

Tenant: default
Username: mifos
Password: password

## Dataset

The file `mifos.json` contains functional descriptions of every navigable page and workflow in the Mifos web application. Each section maps to a distinct UI page that a QA engineer can navigate to and test. The descriptions cover:

- Client, Group, and Center management
- Loan, Savings, Share, and Deposit account lifecycles
- Product configuration (Loan, Savings, Share, Charges, Floating Rates)
- Accounting (Chart of Accounts, Journal Entries, Closures, Rules, Provisioning)
- Organization setup (Offices, Employees, Tellers, Holidays, Currencies)
- Administration (Users, Roles, Scheduler, Configuration, Audit Trails)
- Reports, Account Transfers, Tax Management

These descriptions serve as input for a multi-agent system that generates positive, negative, and edge test cases for automated web testing research.