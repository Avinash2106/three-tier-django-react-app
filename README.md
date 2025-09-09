# Three-Tier Django + React App Deployment

This repository provides a template for deploying a three-tier web application using Docker Compose and Ansible:

- **Backend**: Python Django (example: [django-react-boilerplate-backend](https://github.com/aviyadav/django-react-boilerplate))
- **Frontend**: React (example: [django-react-boilerplate-frontend](https://github.com/aviyadav/django-react-boilerplate))
- **Database**: PostgreSQL

## Usage

### 1. Docker Compose Deployment

Sensitive variables are **not hardcoded** in the compose file and must be passed at runtime.

#### Steps:

```sh
export POSTGRES_PASSWORD=your_db_password
export DJANGO_SECRET_KEY=your_django_secret
docker-compose up -d
```

- The backend (Django) runs on port `8000`.
- The frontend (React) runs on port `3000`.

### 2. Ansible Playbook Deployment

You can use the provided playbook to set up the stack on a remote server.

#### Inventory Example (`hosts`):

```
[appserver]
your.server.ip.address
```

#### Steps:

1. Set your secrets as environment variables on your control node:
   ```sh
   export POSTGRES_PASSWORD=your_db_password
   export DJANGO_SECRET_KEY=your_django_secret
   ```
2. Run the playbook:
   ```sh
   ansible-playbook -i hosts ansible/site.yml
   ```

## Notes

- The Docker Compose file references public images for demo purposes. You may replace these with your own.
- No sensitive information is stored in the repository.
- For production use, ensure your secrets are stored and passed securely.

## References

- [Django React Boilerplate](https://github.com/aviyadav/django-react-boilerplate)
- [PostgreSQL Docker Hub](https://hub.docker.com/_/postgres)
