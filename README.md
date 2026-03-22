# Sanchvi Studio

A Django-based e-commerce and operations platform for fashion retail, built to manage storefront sales, payments, order flow, and internal business tools from one codebase.

## Project Snapshot

Sanchvi Studio combines customer-facing commerce and internal operations in a single Django project.

Primary capabilities:

- Product browsing by category
- Variant-based purchase flow (size/color)
- Cart, checkout, shipping, and order management
- Multi-gateway payments (PayPal + PhonePe)
- Account management and password recovery
- Admin dashboard, maintenance mode, and product control
- Tailor timesheet and salary calculator module

## Feature Matrix

| Module | Purpose | Status |
| --- | --- | --- |
| Accounts | Signup, login, user profile, role-based user model | Active |
| Products | Categories, products, pricing by size, color palette, media | Active |
| Cart | Add/remove items, quantity updates, shipping rate logic | Active |
| Payments | PayPal and PhonePe integration flow | Active |
| Orders | Order creation, order history, confirmation flow | Active |
| Message | Forgot password OTP flow and order emails | Active |
| Admin | Product/admin operations, maintenance controls, analytics | Active |
| Salary_Calculator | Tailor attendance/time and salary calculation | Active |

## Interactive Project Map

Mark completed sections as you explore the codebase:

- [ ] Core Django project (`Sanchvi/`)
- [ ] User and auth flow (`Accounts/`)
- [ ] Product catalog (`Products/`)
- [ ] Cart and order flow (`Cart/`)
- [ ] Payment integration (`Payments/`)
- [ ] Password/email module (`Message/`)
- [ ] Admin panel and tools (`Admin/`)
- [ ] Salary calculator (`Salary_Calculator/`)
- [ ] Templates (`templates/`)
- [ ] Static assets (`static/`)

<details>
<summary><strong>Click to expand service highlights</strong></summary>

- `Sanchvi/`: project settings, URL routing, WSGI/ASGI
- `Accounts/`: custom user model and auth handlers
- `Products/`: inventory entities and catalog presentation
- `Cart/`: cart persistence and checkout orchestration
- `Payments/`: transaction callbacks and payment success handling
- `Admin/`: business operations dashboard and controls
- `Message/`: OTP verification and transactional email routines
- `Salary_Calculator/`: weekly attendance and payout logic

</details>

## Route Overview

Top-level route groups:

- `/` and `/home/`: storefront and home content
- `/auth/`: login/signup/profile/settings
- `/in/`: product dashboard, details, search
- `/cart/`: cart, checkout, orders, shipping APIs
- `/payment/`: payment handlers and confirmation pages
- `/admin/`: custom business admin panel
- `/MSG/`: forgot password and verification flow
- `/time/`: tailor management and salary calculator

## Architecture Overview

Application style:

- Monolithic Django application with modular domain apps
- Server-side rendered templates
- Django ORM data layer with SQLite default
- Payment gateway integration at checkout layer

Domain flow (simplified):

1. User browses products and variants.
2. Cart stores selected product/size/color/qty.
3. Checkout captures shipping and computes shipping charges.
4. User pays via gateway.
5. System creates order and order items.
6. Confirmation page and email are generated.

## Tech Stack

Backend:

- Python
- Django 5.1.1

Commerce/Payments:

- django-paypal
- PhonePe API integration

Frontend:

- Django templates
- HTML/CSS/JavaScript
- Bootstrap/Kaiadmin assets

Runtime/infra:

- Gunicorn
- Nginx (deployment environment)

Libraries used in project:

- Pillow (image handling)
- Requests (external API calls)
- pyOpenSSL / cryptography

## Local Development Setup

1. Clone and enter project

```bash
git clone <your-repo-url>
cd Sanchvi-main
```

2. Create virtual environment

```bash
python -m venv env
```

3. Activate environment

- Windows PowerShell:

```powershell
.\env\Scripts\Activate.ps1
```

- Linux/macOS:

```bash
source env/bin/activate
```

4. Install dependencies

```bash
pip install -r req.txt
```

5. Apply database migrations

```bash
python manage.py migrate
```

6. Create admin user (optional)

```bash
python manage.py createsuperuser
```

7. Run development server

```bash
python manage.py runserver
```

## Environment Variables (Recommended)

The current codebase includes settings currently defined inside project settings. For production hardening, move all secrets to environment variables.

Suggested variables:

- `DJANGO_SECRET_KEY`
- `DJANGO_DEBUG`
- `DJANGO_ALLOWED_HOSTS`
- `EMAIL_HOST`
- `EMAIL_PORT`
- `EMAIL_HOST_USER`
- `EMAIL_HOST_PASSWORD`
- `PAYPAL_TEST`
- `PAYPAL_RECEIVER_EMAIL`
- `PHONEPE_MERCHANT_ID`
- `PHONEPE_SALT_KEY`
- `PHONEPE_SALT_INDEX`
- `PHONEPE_PAYMENT_URL`
- `PHONEPE_CALLBACK_URL`

## Common Commands

```bash
python manage.py makemigrations
python manage.py migrate
python manage.py runserver
python manage.py test
python manage.py collectstatic --noinput
```

## Payments Flow

Supported gateways:

- PayPal
- PhonePe

Checkout summary:

1. Shipping details are captured and validated.
2. Shipping rates are computed by country and package size.
3. User is redirected to selected payment method.
4. Success handlers create order and order items.
5. Cart is cleared after successful order creation.
6. Confirmation page and email are triggered.

## Deployment Notes

Production baseline:

- Django app served via Gunicorn
- Reverse proxy through Nginx
- Static files collected to `staticfiles/`
- Domain setup with allowed hosts configured

Pre-deployment checklist:

1. Set `DEBUG=False`
2. Move secrets to environment variables
3. Configure secure headers and HTTPS
4. Run `collectstatic`
5. Verify payment callback URLs

## Screenshots (Add Your Media)

Recommended screenshots for this README:

1. Home storefront
2. Product detail page
3. Cart and checkout page
4. Payment page
5. Order confirmation
6. Admin dashboard
7. Salary calculator dashboard

## Known Limitations

- Some environment-sensitive settings are currently hardcoded and should be externalized.
- Payment reconciliation and callback verification can be expanded with additional logging.
- Automated test coverage is currently minimal and should be increased.

## Roadmap

- [ ] Move all secrets to environment variables
- [ ] Add CI workflow (lint + test + Django checks)
- [ ] Add stronger admin action auditing
- [ ] Improve payment status reconciliation
- [ ] Add test coverage for checkout and payments
- [ ] Add API documentation and architecture diagram

## Contributing

Contributions are welcome.

Suggested workflow:

1. Fork the repository
2. Create a feature branch
3. Commit with clear messages
4. Open a pull request with description and screenshots

## License

Project-specific licensing details should be defined by repository owner.

## Maintainer Notes

- Keep secrets out of source control.
- Review admin-only operations before production deployment.
- Validate payment configs and callback URLs after each release.
