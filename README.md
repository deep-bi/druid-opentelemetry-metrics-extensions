<!--
  ~ Licensed to the Apache Software Foundation (ASF) under one
  ~ or more contributor license agreements.  See the NOTICE file
  ~ distributed with this work for additional information
  ~ regarding copyright ownership.  The ASF licenses this file
  ~ to you under the Apache License, Version 2.0 (the
  ~ "License"); you may not use this file except in compliance
  ~ with the License.  You may obtain a copy of the License at
  ~
  ~   http://www.apache.org/licenses/LICENSE-2.0
  ~
  ~ Unless required by applicable law or agreed to in writing,
  ~ software distributed under the License is distributed on an
  ~ "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
  ~ KIND, either express or implied.  See the License for the
  ~ specific language governing permissions and limitations
  ~ under the License.
  -->

# OpenTelemetry Extensions

The [OpenTelemetry](https://opentelemetry.io/) extensions provides the ability to read metrics in OTLP format

## Installation and configuration

To install the extension:

1. Extract and copy `druid-opentelemetry-metrics-extensions` into your Druid `extensions` directory.
2. Edit `conf/_common/common.runtime.properties` to add `"druid-opentelemetry-metrics-extensions"` to `druid.extensions.loadList` 
   parameter. It should look like: 

   ```
   druid.extensions.loadList=[..., "druid-opentelemetry-metrics-extensions"]
   ```
   There typically will be a few other extensions there too.

3. Restart your Druid cluster.

## Data source configuration

After enabling the extension in `common.runtime.properties` you can submit a new Supervisor config with
[source input format](https://druid.apache.org/docs/latest/ingestion/data-formats/) as:

```
"ioConfig": {
  "topic": "topic_name",
  "inputFormat": {
    "type": "opentelemetry-metrics-protobuf",
    "metricDimension": "name"
  }
  .
  .
  .
}
```

## Supported Types
### Metric Types:
* SUM
* GAUGE

### Data Types:
* INT_VALUE:
* BOOL_VALUE:
* DOUBLE_VALUE:
* STRING_VALUE:
