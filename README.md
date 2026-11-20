# Bio Attendance — Server

Django backend for the Bio Attendance system.

## Quick Start

i may need to make a script to automate this

```bash
cd server
python3 -m venv venv
source venv/bin/activate
pip install -r requirements/dev.txt
cp .env.example .env
# Edit .env with your database credentials
python manage.py migrate
python manage.py createsuperuser


python manage.py runserver 0.0.0.0:8000
```
dd
## Environment Variables

See `.env.example` for all required variables.

## Running Tests

```bash
pytest
```

## Local Docker Testing

To test the application locally using Docker (with Nginx), make sure you copy `.env.prod.example` to `.env.prod` and configure it to point to your local database, then run:

```bash
# Disable BuildKit if you encounter random crashes during build
export DOCKER_BUILDKIT=0
docker compose up --build -d
```

Visit `http://localhost` to view the application running through Nginx.

## Managing the Docker Container

Once your Docker containers are running (either locally or on your VPS), you may need to run Django commands like `migrate` or `createsuperuser`.

**1. Open a Bash shell inside the container:**

```bash
docker exec -it attendance_web bash
```

**2. Run your Django commands:**
_(You will now be inside the `/app` directory within the container)_

```bash
python manage.py migrate
python manage.py createsuperuser
```

**3. Exit the container:**

```bash
exit
```
cb
Alternatively, you can run a single command without entering the shell:

```bash
docker exec -it attendance_web python manage.py createsuperuser
```
ffzxccv


i need to think about a backup stratigy this one is very important
