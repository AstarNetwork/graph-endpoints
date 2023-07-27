# Subgraph

 1. [Credentials](#credentials)
 2. [Endpoints](#endpoints)
 3. [Deployment](#deployment)
 4. [Monitoring](#monitoring)

## [Credentials](#subgraph)

In order to start to use **TheGraph-Astar** infrastructure you will receive the credentials to be able to authenticate in the endpoints. These include:
 - Username
 - Password
 - Basic Authentication

## [Endpoints](#subgraph)

**DEV**

| Endpoint                                           | Description           |
| ---------------------------------------------------| --------------------- |
| https://grafana-dev.graph.astar.network            | Grafana               |
| https://ipfs-dev.graph.astar.network               | IPFS node             |
| https://index-shibuya.graph.astar.network  | Indexer node Shibuya  |
| https://query-shibuya.graph.astar.network          | Query node Shibuya    |

**PROD**

| Endpoint                                   | Description         |
| -------------------------------------------| --------------------|
| https://grafana-prod.graph.astar.network   | Grafana             |
| https://ipfs-prod.graph.astar.network      | IPFS node           |
| https://index-astar.graph.astar.network    | Indexer node Astar  |
| https://query-astar.graph.astar.network    | Query node Astar    |
| https://index-shiden.graph.astar.network   | Indexer node Shiden |
| https://query-shiden.graph.astar.network   | Query node Shiden   |

## [Deployment](#subgraph)

Once you have got the credentials you'll be able to deploy your subgraph in **TheGraph-Astar** infrastructure in two ways:

 1. [Manually](#manually)
 2. [Automatically](#automatically)

### [Manually](#deployment)

Please follow the above steps:

 1. Depending on your subgraph code you may also need to run:
 ```
  yarn install
  yarn codegen
  yarn build
 ```

 2. Graph Create
 ```bash
 graph create <SUBGRAPH_NAME> --version-label <SUBGRAPH_NAME> --headers "{\"Authorization\": \"Basic <BASIC_AUTH>\"}" --ipfs https://ipfs-dev.graph.astar.network --node https://<USERNAME>:<PASSWORD>@index-shibuya.graph.astar.network
 
 Created subgraph: <SUBGRAPH_NAME>
 ```
 > Note: On graph-cli version 0.42.1 and above you only need to set the _--node_ flag
 ```bash
 graph create <SUBGRAPH_NAME> --node https://<USERNAME>:<PASSWORD>@index-shibuya.graph.astar.network
 ```



 3. Graph Deploy
    
 ```bash
 graph deploy <SUBGRAPH_NAME> --version-label <SUBGRAPH_NAME> --headers "{\"Authorization\": \"Basic <BASIC_AUTH>\"}" --ipfs https://ipfs-dev.graph.astar.network --node https://<USERNAME>:<PASSWORD>@index-shibuya.graph.astar.network
 ```


### [Automatically](#deployment)

You can use the workflow ***[ASTAR] - Build and Deploy Subgraph*** with all the basic steps to deploy your subgraph automatically.

You can find the workflow [here](https://github.com/protofire/astar-infra/blob/main/.github/workflows/subgraph-deploy.yaml)

The pipeline will ask you the following input data:

 - Username
 - Password
 - Basic_Auth
 - Subgraph_Name
 - Repository
 - Branch
 - ipfs_endpoint
 - index_node_endpoint

> **_NOTE_**: You can customize the workflow in order to include additional steps based on your subgraph code. You can also modify it in order to be triggered based on a specific event (such as push, tag, label)

## [Monitoring](#subgraph)

Once you have created and deployed your subgraph you can see the ***Indexing Status Overview*** dashboard in grafana.

Using the same credentials (Username & Password) you previously received you can access Grafana portal in the following URL:

**DEV**
https://grafana-dev.graph.astar.network

**PROD**
https://grafana-prod.graph.astar.network 


