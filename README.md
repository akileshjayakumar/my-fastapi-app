# FastAPI + Celery Async Task API

Run asynchronous arithmetic jobs with FastAPI, Celery, RabbitMQ, Redis, and Flower using a single Docker Compose command.

## Quick Start

```bash
git clone https://github.com/akileshjayakumar/my-fastapi-app
cd my-fastapi-app
docker compose up --build
```

After startup:
- API docs: [http://localhost:8000/docs](http://localhost:8000/docs)
- Flower dashboard: [http://localhost:5555](http://localhost:5555)
- RabbitMQ management: [http://localhost:15672](http://localhost:15672) (`guest` / `guest`)

## Core Capabilities

- Queue `add` and `multiply` tasks asynchronously
- Retrieve task status/results by task ID
- Monitor workers and task activity in Flower
- Run the full stack in containers (web, worker, broker, backend, monitor)

## Configuration

No environment variables are required for the default Docker Compose setup.

Default service URLs used by the app:
- Broker: `amqp://rabbitmq:5672//`
- Result backend: `redis://redis:6379/0`

If you need different infrastructure, update `app/tasks.py`.

## Usage

Submit an addition task:

```bash
curl -X POST http://localhost:8000/add/3/4
```

Submit a multiplication task:

```bash
curl -X POST http://localhost:8000/multiply/6/7
```

Both endpoints return:

```json
{"task_id":"<id>"}
```

Check task status/result:

```bash
curl http://localhost:8000/result/<task_id>
```

Possible responses include:
- `{"status":"PENDING"}`
- `{"status":"SUCCESS","result":42}`
- `{"status":"FAILURE","error":"..."}`

## Contributing and Testing

Contributions are welcome through issues and pull requests.

There is no automated test suite yet. Use this manual smoke test:

1. Start services with `docker compose up --build`.
2. Call `POST /add/2/5` and copy the returned `task_id`.
3. Poll `GET /result/<task_id>` until status is `SUCCESS`.

Stop services:

```bash
docker compose down
```

## Architecture

![Architecture Diagram](diagram.png)

## License

MIT. See `LICENSE`.
