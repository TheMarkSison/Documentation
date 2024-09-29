# Getting Started.

## Django.

Create a Virtual Environment and installing Django.

```shell
# Create Virtual Environment.
python3 -m venv .venv

# Activate Virtual Environment.
source .venv/bin/activate

pip install django
pip install psycopg2      # Postgres.
pip install python-dotenv # Environment Variables.
```
  
Create a new Django Project and Application.

```shell
# Create a new Django Project in your current directory.
django-admin startproject <PROJ_NAME> .

# Create a Django Application.
python manage.py createapp <APP_NAME>
```

Connecting to the Postgres Database using a `.env` file.

`.env`

```
DB_NAME=<DB_NAME>
DB_USER=<DB_USER>
DB_PASS=<DB_PASS>
DB_HOST=<DB_HOST>
DB_PORT=<DB_POST>
```

`settings.py`

You need to update the `DATABASE` setting to connect to the Postgres database using
the environment variables.

```python
from dotenv import load_dotenv
import os

load_dotenv()

# Other Settings omitted.

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': os.getenv('DB_NAME'), 
        'USER': os.getenv('DB_USER'),
        'PASS': os.getenv('DB_PASS'),
        'HOST': os.getenv('DB_HOST'), 
        'PORT': os.getenv('DB_PASS'),
    }
}
```