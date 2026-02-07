# FastAPI + Celery Async Task API
Run asynchronous arithmetic jobs with FastAPI, Celery, RabbitMQ, Redis, and Flower using a single Docker Compose command.

## Quick Start
```bash
git clone https://github.com/akileshjayakumar/my-fastapi-app
cd my-fastapi-app
docker compose up --build
```

## Capabilities
- API docs: [http://localhost:8000/docs](http://localhost:8000/docs)
- Flower dashboard: [http://localhost:5555](http://localhost:5555)
- RabbitMQ management: [http://localhost:15672](http://localhost:15672) (`guest` / `guest`)
- Queue `add` and `multiply` tasks asynchronously

## Configuration
- No required environment variables are documented for basic usage.

## Usage
```bash
curl -X POST http://localhost:8000/add/3/4
```

## Contributing and Testing
- Contributions are welcome through pull requests with clear, scoped changes.
- Run the following checks before submitting changes:
```bash
python -m pytest
```

## License
Licensed under the `MIT` license. See [LICENSE](./LICENSE) for full text.
