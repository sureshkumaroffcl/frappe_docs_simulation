# Exporting Users in ERPNext

ERPNext allows exporting data from the UI, but sometimes you may want to use a **Python script** for automation or bulk operations.  
This guide explains how to export User details programmatically using Frappe.

---

## 📌 Python Script Example

import frappe

def export_users():
    users = frappe.get_all("User", fields=["name", "email", "enabled"])
    with open("users_export.csv", "w") as f:
        f.write("Name,Email,Enabled\n")
        for u in users:
            f.write(f"{u.name},{u.email},{u.enabled}\n")

if __name__ == "__main__":
    export_users()


---

## 📝 Output Format

```
Name,Email,Enabled
Administrator,admin@example.com,1
John Doe,john@example.com,1
Jane Doe,jane@example.com,0
```

---

## ✅ Use Cases

* Automated backups of user records  
* Migration between ERPNext instances  
* Auditing enabled/disabled user accounts
