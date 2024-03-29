# Lacework

{% hint style="info" %}
Required fields are in **bold**.
{% endhint %}

## Lacework.Events

Lacework.Events represents the content of an exported Lacework Alert S3 Object. Reference: [https://www.lacework.com/platform-overview/](https://www.lacework.com/platform-overview/)

| Column | Type | Description |
| :--- | :--- | :--- |
| **`EVENT_CATEGORY`** | `string` | The category the event falls into |
| **`EVENT_DETAILS`** | `{   "data":[{     "START_TIME":timestamp,     "END_TIME":timestamp,     "EVENT_TYPE":string,     "EVENT_ID":string,     "EVENT_ACTOR":string,     "EVENT_MODEL":string,     "ENTITY_MAP":{       "User":[{         "MACHINE_HOSTNAME":string,         "USERNAME":string }],       "Application":[{         "APPLICATION":string,         "HAS_EXTERNAL_CONNS":bigint,         "IS_CLIENT":bigint,         "IS_SERVER":bigint,         "EARLIEST_KNOWN_TIME":timestamp }],       "Machine":[{         "HOSTNAME":string,         "EXTERNAL_IP":string,         "INSTANCE_ID":string,         "INSTANCE_NAME":string,         "CPU_PERCENTAGE":float,         "INTERNAL_IP_ADDR":string,         "IS_EXTERNAL":bigint }],       "Container":[{         "IMAGE_REPO":string,         "IMAGE_TAG":string,         "HAS_EXTERNAL_CONNS":bigint,         "IS_CLIENT":bigint,         "IS_SERVER":bigint,         "FIRST_SEEN_TIME":timestamp,         "POD_NAMESPACE":string,         "POD_IP_ADDR":string }],       "DnsName":[{         "HOSTNAME":string,         "PORT_LIST":[int],         "TOTAL_IN_BYTES":float,         "TOTAL_OUT_BYTES":float }],       "IpAddress":[{         "IP_ADDRESS":string,         "TOTAL_IN_BYTES":float,         "TOTAL_OUT_BYTES":float,         "THREAT_TAGS":[string],         "THREAT_SOURCE":string,         "COUNTRY":string,         "REGION":string,         "PORT_LIST":[int],         "FIRST_SEEN_TIME":string }],       "Process":[{         "HOSTNAME":string,         "PROCESS_ID":bigint,         "PROCESS_START_TIME":timestamp,         "CMDLINE":string,         "CPU_PERCENTAGE":float }],       "FileDataHash":[{         "FILEDATA_HASH":string,         "MACHINE_COUNT":bigint,         "EXE_PATH_LIST":[string],         "FIRST_SEEN_TIME":timestamp,         "IS_KNOWN_BAD":bigint }],       "FileExePath":[{         "EXE_PATH":string,         "FIRST_SEEN_TIME":timestamp,         "LAST_FILEDATA_HASH":string,         "LAST_PACKAGE_NAME":string,         "LAST_VERSION":string,         "LAST_FILE_OWNER":string }],       "SourceIpAddress":[{         "IP_ADDRESS":string,         "REGION":string,         "COUNTRY":string }],       "API":[{         "SERVICE":string,         "API":string }],       "Region":[{         "REGION":string,         "ACCOUNT_LIST":[string] }],       "CT_User":[{         "USERNAME":string,         "ACCOUNT_ID":string,         "MFA":bigint,         "API_LIST":[string],         "REGION_LIST":[string],         "PRINCIPAL_ID":string }],       "Resource":[{         "NAME":string,         "VALUE":string }],       "RecId":[{         "REC_ID":string,         "ACCOUNT_ID":string,         "ACCOUNT_ALIAS":string,         "TITLE":string,         "STATUS":string,         "EVAL_TYPE":string,         "EVAL_GUID":string }],       "CustomRule":[{         "LAST_UPDATED_TIME":timestamp,         "LAST_UPDATED_USER":string,         "DISPLAY_FILTER":string,         "RULE_GUID":string }],       "NewViolation":[{         "REC_ID":string,         "REASON":string,         "RESOURCE":string }],       "ViolationReason":[{         "REC_ID":string,         "REASON":string }] } }] }` | The event details |
| **`SEVERITY`** | `bigint` | The severity level of the alert |
| **`START_TIME`** | `timestamp` | The event start time. |
| **`SUMMARY`** | `string` | The alert title and quick summary |
| **`EVENT_TYPE`** | `string` | The type of event |
| **`EVENT_NAME`** | `string` | The event name |
| **`LINK`** | `string` | A link to the Lacework dashboard for the event |
| **`EVENT_ID`** | `bigint` | The eventID reference |
| **`ACCOUNT`** | `string` | The Lacework tenent that created the event |
| **`SOURCE`** | `string` | The data source the event triggered on |
| **`p_log_type`** | `string` | Panther added field with type of log |
| **`p_row_id`** | `string` | Panther added field with unique id \(within table\) |
| **`p_event_time`** | `timestamp` | Panther added standardize event time \(UTC\) |
| **`p_parse_time`** | `timestamp` | Panther added standardize log parse time \(UTC\) |
| `p_source_id` | `string` | Panther added field with the source id |
| `p_source_label` | `string` | Panther added field with the source label |
| `p_any_ip_addresses` | `[string]` | Panther added field with collection of ip addresses associated with the row |
| `p_any_domain_names` | `[string]` | Panther added field with collection of domain names associated with the row |
| `p_any_sha1_hashes` | `[string]` | Panther added field with collection of SHA1 hashes associated with the row |
| `p_any_md5_hashes` | `[string]` | Panther added field with collection of MD5 hashes associated with the row |
| `p_any_sha256_hashes` | `[string]` | Panther added field with collection of SHA256 hashes of any algorithm associated with the row |

