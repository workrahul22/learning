Functional Requirements
    1. upload
    2. watch videos

Non Functional Requirements
    1. Reliability
    2. Scale 1B DAU watching 5/day
    3. Availability > Consistency
    4. Minimise Latency

High Level Design

```mermaid
    flowchart LR
        subgraph client
            User
        end
        subgraph LB
            LoadBalancer
        end
        subgraph app
            APP
            APP1
            APP2
            Encoding
        end
        subgraph store
            ObjectStorage[(Object Storage)]
            NoSql[(NoSQL Metadata structure)]
            Cache[(Redis Cache)]
        end

        subgraph queue
            queue
        end

        User --> LoadBalancer
        LoadBalancer --> APP
        LoadBalancer --> APP1
        LoadBalancer --> APP2
        APP --> ObjectStorage
        APP1 --> ObjectStorage
        APP2 --> ObjectStorage
        APP --> NoSql
        APP1 --> NoSql
        APP2 --> NoSql
        APP --> Cache
        APP1 --> Cache
        APP2 --> Cache
        ObjectStorage --> queue
        queue --> Encoding
```