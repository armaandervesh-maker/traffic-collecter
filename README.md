# Traffic Collector

This public repository runs a small GitHub Actions schedule for the traffic-prediction project.

## What it does

Every 5 minutes, GitHub Actions sends an authenticated POST request to the private traffic API's collection endpoint.

The private API then:

- fetches current TomTom traffic for the monitored roads
- saves the traffic readings to Supabase
- evaluates eligible 30-minute predictions
- creates new 30-minute ML predictions

## Security

No API keys, database passwords, or collector credentials are stored in this repository.

The workflow uses two GitHub Actions repository secrets:

- `COLLECT_URL`
- `COLLECTOR_TRIGGER_SECRET`

The main traffic prediction application remains in a private repository.
