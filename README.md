# compclub-web

Dependencies:
- [Python 3.6+](https://python.org)
- [pipenv](https://github.com/pypa/pipenv). Pipenv takes care of installing and managing Python dependencies.

## Development

### Install Dependencies

```sh
pipenv install
```

### Initialize Database
```sh
pipenv run python manage.py migrate
```

### Run the server
```sh
pipenv run python manage.py runserver
```

This will start a development server with automatic reloading on code changes

## Deploying 

The app is built using Docker. The container has the following attributes:

### Volumes:
 - `/data`: Data volume for the app. Contains sqlite db.

### Ports:
The container exposes the server on port 8080.

### Environment:
You must provide the following environment variables

 - `SECRET_KEY`: The secret key used to sign cookies.

### Run the container 

```sh
docker run --rm -it --name compclub-web -p 8080:8080 \
  -v $PWD/data:/data \
  -e SECRET_KEY="replaceme" \
  csesoc/compclub-web
```

## Building the Docker Container
```sh
# Build the container
docker build -t csesoc/compclub-web .

# Push the container
docker push csesoc/compclub-web
```
