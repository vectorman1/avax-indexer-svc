# Avax Indexing Service

## Overview

The Avax Indexing Service is a service that indexes the Avalanche blockchain and provides a queryable API for retrieving
information about the blockchain and its contents.

The submodules of this repository are:

- [avax-indexer](https://github.com/vectorman1/avax-indexer): a Go-based service that indexes the Avalanche blockchain
  and stores the data in a MongoDB database
- [avax-indexer-api](https://github.com/vectorman1/avax-indexer-api): a Nest-based API that wraps the data created by
  the indexer and exposes some endpoints regarding transactions and active addresses

The API includes an OpenAPI Swagger specification which can be accessed at the base url once launched.

### Prerequisites

- Docker
- Docker Compose

### Steps

1. Clone the repository
2. Run `git submodule update --init --recursive` to initialize the submodules
3. Set your own Infura API key for Avalanche network of choice under `indexer.environment.AVAX_RPC_INFURA` in
   the `docker-compose.yml` file. A key can be acquired [here](https://app.infura.io/).
4. Run `docker compose up -d` to start the service
5. Run `docker compose logs -f` to view the logs
6. Access the API at `http://localhost:3000`

**NB**: Initial catchup of the indexer can take about a minute. Logs of
the [indexer](https://github.com/vectorman1/avax-indexer) will show the progress. Afterwards, each time it is restarted,
it will catch up with the missed out blocks.

