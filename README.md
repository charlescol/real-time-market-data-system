# Market Streaming Infrastructure

This repository groups the main components used to deploy, run, and analyze a distributed real-time market-data pipeline. The system ingests live exchange updates, reconstructs order-book state, computes derived streams, and supports offline analysis of the resulting data.

The project is accompanied by a technical-note series documenting the design, implementation, operational behavior, and timing effects of the pipeline. See [Technical Notes](#technical-notes).

## Components

### Order Book Engine and Feature Extractor

- [Order Book Engine and Feature Extractor](https://github.com/charlescol/market-streaming-infra-flink-microstructures-extractor)  
  Flink-based processing component that reconstructs order-book state and computes derived microstructure features.

### Feed Handlers

- [KuCoin Feed Handler](https://github.com/charlescol/market-streaming-infra-msv-tokio-kucoin-scraper)  
  Tokio-based service for ingesting KuCoin live market-data updates.

- [Binance Feed Handler](https://github.com/charlescol/market-streaming-infra-msv-tokio-binance-scraper)  
  Tokio-based service for ingesting Binance live market-data updates.

### Snapshot Middleware

- [KuCoin Snapshot Middleware](https://github.com/charlescol/market-streaming-infra-tokio-kucoin-snapshot-middleware)  
  Middleware service for retrieving and serving KuCoin order-book snapshots used during stream initialization and recovery.

- [Binance Snapshot Middleware](https://github.com/charlescol/market-streaming-infra-tokio-binance-snapshot-middleware)  
  Middleware service for retrieving and serving Binance order-book snapshots used during stream initialization and recovery.

## Infrastructure

- [GitOps](https://github.com/charlescol/market-streaming-infra-gitops)  
  Deployment configuration and GitOps manifests for operating the system.

- [Infrastructure as Code](https://github.com/charlescol/market-streaming-infra-terraform)  
  Terraform configuration for provisioning the underlying infrastructure.

- [Project Generated Protobuf Code](https://github.com/charlescol/market-streaming-infra-schema-core)  
  Generated Protobuf code packages shared by the market-data pipeline components.

- [Schema Deployment](https://github.com/charlescol/market-streaming-infra-schema-registry)  
  Schema Registry deployment and related configuration.

- [Binance Generated SBE Code](https://github.com/charlescol/market-streaming-infra-schema-binance)  
  Binance SBE schema definitions used for decoding exchange messages.

## Offline Analysis

- [Data Analysis Infrastructure](https://github.com/charlescol/market-streaming-infra-post-processing)  
  Infrastructure and tooling for offline processing and analysis of stored pipeline data.

- [Data Queries](https://github.com/charlescol/market-streaming-infra-post-processing-queries)  
  Query definitions used for post-processing, empirical analysis, and technical-note figures.

## Technical Notes

### Technical Note #1: Design Trade-offs and Failure Modes in a Real-Time Market Data Pipeline [[PDF](https://doi.org/10.5281/zenodo.20307754)]

This note analyzes the pipeline design and its behavior under saturation, recovery, and failure conditions.

### Technical Note #2: On the Temporal Structure of Distributed Pipelines [[PDF](https://doi.org/10.5281/zenodo.20310667)]

This note analyzes the temporal behavior of the pipeline, focusing on how processing delays, timing gaps, bursts, and compression affect downstream signals.
