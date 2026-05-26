
# Stored Procedure Naming Conventions (SQL Server)

## General Rules
- Stored procedure names must be **descriptive and consistent**
- Always **schema‑qualify** stored procedure calls (e.g. `dbo.usp_MyProcedure`)
- Naming conventions are **standards**, not SQL Server requirements

## Approved Prefixes

| Prefix | Purpose |
|------|--------|
| `usp_` | User‑defined stored procedures (general purpose) |
| `rpt_` | Reporting / read‑only procedures |
| `app_` | Application‑specific business logic |
| `gen_` | General utilities or CRUD‑style procedures |

 Example:
```sql
dbo.usp_SAP_COH_Undeposited_Cash_Monthly
```
## Do NOT name user‑defined stored procedures with the sp_ prefix.
Why this is discouraged:
- SQL Server applies special name resolution rules to procedures starting with sp_
- SQL Server checks master database first, then the current database
- This causes:
    - Unnecessary lookup overhead
    - Possible performance impact on frequent calls
    - Risk of name collisions with future system procedures
    - Confusion with system‑defined stored procedures


📌 This behavior is documented and intentional in SQL Server.
---                             
# Commit Message Template

| Prefix      | Purpose                                                         |
| -------------| -----------------------------------------------------------------|
| `feat:`     | A new feature                                                   |
| `fix:`      | A bug fix                                                       |
| `refactor:` | Code change that neither fixes a bug nor adds a feature         |
| `chore:`    | Maintenance tasks (dependency updates, config changes, tooling) |
| `docs:`     | Documentation only changes                                      |
| `style:`    | Formatting, missing semicolons, whitespace — no logic change    |
| `test:`     | Adding or updating tests                                        |
| `perf:`     | Performance improvements                                        |
| `ci:`       | CI/CD configuration changes                                     |
| `build:`    | Changes to build system or external dependencies                |
| `revert:`   | Reverts a previous commit                                       |

---

# Pull Request Template

```md
# Pull Request

## Description

Added SQL procedures required for daily auto receipt generation/Daily EJ needed by pickup/pre-commit transactions .

## Type of change

Please put an `x` in the boxes that apply:

- [ ] **Bug fix** (non-breaking change which fixes an issue)
- [x] **New feature** (non-breaking change which adds functionality)
- [ ] **Breaking change** (fix or feature that would cause existing functionality to not work as expected)
- [ ] **Documentation update** (non-breaking change; modified files are limited to the documentations)
- [ ] **Technical debt** (a code change that does not fix a bug or add a feature but makes something clearer for devs)
- [ ] **Other** (provide details below)
```
---
