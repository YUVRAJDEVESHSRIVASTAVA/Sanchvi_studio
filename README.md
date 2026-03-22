# Sanchvi - Django E-commerce Platform

A full-stack Django project with user accounts, products, cart, payments, messaging, and admin modules.

## Quick Start

1. **Clone and enter project**
   ```bash
   git clone <your-repo-url>
   cd Sanchvi-main
   ```

2. **Create virtual environment**
   ```bash
   python -m venv env
   ```

3. **Activate virtual environment**
   - Windows (PowerShell):
     ```powershell
     .\\env\\Scripts\\Activate.ps1
     ```
   - Linux/macOS:
     ```bash
     source env/bin/activate
     ```

4. **Install dependencies**
   ```bash
   pip install -r req.txt
   ```

5. **Run migrations**
   ```bash
   python manage.py migrate
   ```

6. **Start development server**
   ```bash
   python manage.py runserver
   ```

7. **Open in browser**
   http://127.0.0.1:8000/

---

## Interactive Project Map

Use this checklist to track what you have explored:

- [ ] Accounts module (`Accounts/`)
- [ ] Products module (`Products/`)
- [ ] Cart module (`Cart/`)
- [ ] Payments module (`Payments/`)
- [ ] Messaging module (`Message/`)
- [ ] Admin module (`Admin/`)
- [ ] Templates (`templates/`)
- [ ] Static assets (`static/`)

<details>
<summary><strong>Click to view folder highlights</strong></summary>

- `Sanchvi/`: core Django settings, URLs, WSGI/ASGI setup
- `Accounts/`: authentication, user profile logic, middleware
- `Products/`: product models, filters, forms, views
- `Cart/`: cart workflow
- `Payments/`: payment-related models and views
- `templates/`: UI pages grouped by feature
- `static/`: CSS, JS, image assets

</details>

---

## Common Commands

```bash
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
python manage.py test
```

---

## Notes

- Keep secrets in `.env` (never commit it).
- Current ignore rules are defined in `.gitignore`.
- This README is intentionally interactive so new contributors can onboard quickly.
