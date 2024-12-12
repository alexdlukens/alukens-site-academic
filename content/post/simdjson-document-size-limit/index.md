---
title: simdjson Document Size Limit
date: 2023-02-21T02:42:52.179Z
draft: false
featured: false
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
During my research of JSON parsing libraries for C++ I came across simdjson: A library that promises 4x faster parsing than [RapidJSON](https://rapidjson.org/). While this library does indeed perform better than other C++ JSON libraries, I ran into an issue with maximum single document size when utilizing this library. Simdjson supports a maximum single document size of 4GB, and defers to using JSONLines to support larger documents as a single, large document should be represented as several smaller, individual documents. 

Until this point, I was utilizing the JSON format as a single, monolithic datastore for [AI knowledge](https://intelligent-artifacts.com), but this limitation caused me to reflect and consider the alternatives. Instead of formatating the knowledgebase as a single document, the same data could be easily formatted into several, smaller and incremental storage documents. This allowed for a simpler parsing mechanism to be used, and increased the robustness of the code. Furthermore, smaller documents lend well for future migrations to using a document-based DB, such as [MongoDB](https://www.mongodb.com/)

This monolithic data store was inadequate for long-term usage, and was destined to be retired, but was instrumental to the overall design of the data structure. The smaller, multi-document implementation of data storage using the [jsonlines format](https://jsonlines.org) has remained to be scalable and has retained usability from the monolithic data structure. In the future, I will keep these limitations in mind, and ensure that applications use an appropriate data storage mechanism when they reach large data thresholds instead of falling back on a single. monolithic file.