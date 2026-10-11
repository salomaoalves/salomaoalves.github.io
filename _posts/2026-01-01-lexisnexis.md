---
layout: post
title: "Work at LexisNexis Risk Solutions"
subtitle: "5 years building ETL pipelines and real-time data products on HPCC Systems"
date: 2026-01-01
header-img: "img/hpcc-architecture.png"
tags: [DataEngineering, ETL, HPCC, ECL, BigData, Backend]
---

> For about five years I worked at **LexisNexis Risk Solutions**, a company whose products in credit risk, fraud prevention and identity verification depend on processing billions of public and proprietary records. I spent almost two years as a **Data Engineer** on an ETL pipeline, then nearly three as a **Backend Developer** on the **Roxie** team, delivering data products in real time.

## The platform: HPCC Systems and ECL

LexisNexis built its own big data platform, **HPCC Systems** (High-Performance Computing Cluster), and open-sourced it in 2011. It predates Spark and solves the same problem in its own way. It has two main components:

- **Thor**: the batch engine. It runs massive ETL/Linking jobs (ingestion, cleaning, transformation, entity linking) across a cluster. It plays a role similar to Hadoop/Spark.
- **Roxie**: the real-time query engine. It serves pre-built, indexed data with sub-second latency to thousands of concurrent requests. It's what customer-facing products query.

Both are programmed in **ECL** (Enterprise Control Language), a **declarative dataflow language**: you describe *what* transformation you want (joins, projections, deduplication, aggregations), and the compiler optimizes and parallelizes it into C++ across the cluster. The mindset is close to SQL or Spark DataFrames, applied to datasets with billions of rows.

```ecl
// Example: deduplicate people by ID, keeping the most recent record
people_sorted := SORT(people, person_id, -last_seen_date);
latest        := DEDUP(people_sorted, person_id);
OUTPUT(latest);
```

## Phase 1 — Data Engineer, ETL team (6/2021–3/2023)

I worked on an ETL pipeline running on Thor that ingests, cleans and standardizes raw data so it can be used by downstream products.

- **Maintained the pipeline and fixed** production bugs (broken transformations, data-quality issues, failures caused by upstream data changes), as well as the data anonymization process
- **Built new features**: new sources, fields, transformation rules and keys used by Roxie
- **Tested at three levels** to make sure changes didn't break the data consumed by other teams

## Phase 2 — Backend Developer, Roxie team (3/2023–1/2026)

On the Roxie team I worked at the point where all the data work becomes a product: the queries customers call in real time.

- **Product integration**: connected the work of every team involved in delivering a product: *ESP/Web* (the service layer exposing queries as APIs), *Data* (the pipelines feeding the indexes), *Analytics* (models and scores) and *Linking* (entity resolution, which determines that different records refer to the same person)
- **Built internal data tools**: wrote custom Roxie queries to extract specific information of internal value (e.g. product usage, data coverage, quality checks) and turned the results into dashboards used by other teams to monitor and make decisions
- **Built new products end-to-end**: developed the Roxie queries behind several data products for financial institutions and other enterprise clients, covering identity verification, fraud risk and credit risk. Each one combined multiple data sources, entity-linking results and analytics scores into a single real-time API response, from ECL implementation through testing to production
- **Fixed production bugs** across this multi-team chain, which meant tracing a problem through data, linking, query and API layers
- **Wrote tests** for queries and integrations using anonymized/masked data

## What I took from it

- Thinking in **datasets, not rows**: declarative, distributed transformations
- **Data quality** matters most in domains like credit and identity, where a bad record means a wrong decision about a real person
- **Batch vs real-time** trade-offs: what to precompute in Thor, what to serve from Roxie
- **Working across teams**: most production issues lived *between* systems, not inside one

## Stack

HPCC Systems (Thor/Roxie) · ECL · ETL · Backend Dev · ESP|Linking · [SQL / Python / Git]