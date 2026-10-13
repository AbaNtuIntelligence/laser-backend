# Laser showcase backend
Standalone Django API. Upload the contents of this folder into a new backend repository.

Render: Python Web Service, Free for showcase only; root directory blank.
Build: `pip install -r requirements.txt && python manage.py collectstatic --noinput`
Start: `python manage.py migrate --noinput && gunicorn config.wsgi:application --bind 0.0.0.0:$PORT --workers 1 --threads 2 --timeout 120`
Health check: `/api/status/`

Environment: PYTHON_VERSION=3.12.14; DEBUG=False; a generated SECRET_KEY; DATABASE_PATH=/tmp/laser-showcase.sqlite3; CORS_ALLOWED_ORIGINS=the exact frontend HTTPS origin; GOOGLE_SHEET_ID=your catalogue spreadsheet ID; GOOGLE_OAUTH_TOKEN_FILE=/etc/secrets/oauth-token.json.
Add your existing authorised Google OAuth JSON as a Render Secret File named `oauth-token.json`. It needs a refresh token and access to the sheet's Products tab. Do not commit it or paste it in chat. The credentials are NOT included in this package. A healthy API alone does not prove that catalogue access is configured.

Free showcase: use fictional quote details only. SQLite quote records disappear on redeploy, restart or idle spin-down. This package does not migrate any live records or configure production persistence.

PDF image assets are bundled under catalogue_assets/images, so this backend no longer needs a sibling frontend folder. Keep these copies updated when replacing catalogue photos.
Admin static files are served with WhiteNoise. No admin account or live credentials are included.

Run `python manage.py check` and `python manage.py test` after installing requirements.
