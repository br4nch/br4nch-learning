1 Item has a limit of 400KB in size, which include both attribute name binary length (UTF-8 length) and attribute value lengths (binary length). The attribute name counts towards the size limit

## DDB Stream
### Stream concept
- Time ordered list of ITEM changes in a table
-  24-hour rolling window
-  Enabled on a per table basis
- Records INSERTS, UPDATES and DELETES
-  Different view types influence what is in the stream
#### 4 View types
- KEYS_ONLY
- NEW_IMAGE
- OLD_IMAGE
- NEW_AND_OLD_IMAGES

### Trigger concept
- Item changes generate an event, contains the data which changed -> An action is taken using that data
- AWS = Streams + Lambda
- Reporting & Analytics
- Aggregation, Messaging or Notifications

Lambda can be integrated to provide trigger functionality - invoking when new entries are added on the stream

### DDB Accelerator (DAX)
- DAX is an **in-memory cache** designed specifically for DynamoDB
- Traditional Cache vs DAX: 3 steps vs 2 steps as application call DAX to retrieve data without worrying about **CACHE MISS** -> **Less complexity** for the app developer - **tighter integration**
- DAX Architecture
	- Multi AZ 
	- Access via an endpoint
	- CACHE HITS are return in microseconds
	- CACHE MISSES are return in milliseconds
	- Write-Through is supported, data is written to DDB then DAX
- DAX Considerations
	- Primary NODE (Writes) and Replicas (Read)
	- Nodes are HA .. Primary failure = election
	- In-memory cache - Scaling ..Much faster reads, reduced costs
	- Scale UP and Scale OUT (Bigger or More)
	- Supports write-through
	- DAX Deployed **Within a VPC**

#aws #dynamodb #ddb #ddb-streams #ddb-triggers #ddb-dax #within-vpc