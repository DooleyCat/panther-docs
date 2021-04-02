# Sophos

{% hint style="info" %}
Required fields are in **bold**.
{% endhint %}

## Sophos.Central

Sophos Central events Reference: [https://support.sophos.com/support/s/article/KB-000038307?language=en\_US](https://support.sophos.com/support/s/article/KB-000038307?language=en_US)

| Column | Type | Description |
| :--- | :--- | :--- |
| **`endpoint_id`** | `string` | Endpoint ID associated with the event |
| **`endpoint_type`** | `string` | Type of endpoint |
| `customer_id` | `string` | Customer ID |
| `severity` | `string` | Severity of the event |
| `source_info` | `{   "ip":string }` | Source IP of the endpoint |
| `name` | `string` | Name of threat, or other event details |
| **`id`** | `string` | Unique identifier for the event |
| **`type`** | `string` | Type of event |
| **`group`** | `string` | Category of event |
| **`end`** | `timestamp` | Time the event occurred on the endpoint |
| `rt` | `timestamp` | Time the event was uploaded to Sophos Central |
| `dhost` | `string` | Source host of the event |
| `suser` | `string` | Logged in user |
| `datastream` | `string` | Alert, or Event, to distinguish between event types |
| `duid` | `string` | Undocumented field |
| `threat` | `string` | Name of the threat |
| `detection_identity_name` | `string` | Name of the detection |
| `filePath` | `string` | Path to the threat |
| `user` | `string` | Undocumented field, but should be same as User |
| `rule` | `string` | DLP rule |
| `user_action` | `string` | DLP user action |
| `app_name` | `string` | DLP application name |
| `action` | `string` | DLP action |
| `file_type` | `string` | DLP file type |
| `file_size` | `bigint` | DLP file size |
| `file_path` | `string` | DLP file path |
| `appSha256` | `string` | SHA 256 hash of the application associated with the threat, if available |
| `appCerts` | `[{   "signer":string,   "thumbprint":string }]` | Certificate information for the application associated with the threat, if available |
| `origin` | `string` | Originating component of a detection |
| `core_remedy_items` | `{   "items":[{     "type":string,     "result":string,     "descriptor":string,     "processPath":string }],   "totalItems":int }` | Details of the items cleaned or restored |
| **`p_event_time`** | `timestamp` | Panther added standardized event time \(UTC\) |
| **`p_parse_time`** | `timestamp` | Panther added standardized log parse time \(UTC\) |
| **`p_log_type`** | `string` | Panther added field with type of log |
| **`p_row_id`** | `string` | Panther added field with unique id \(within table\) |
| `p_source_id` | `string` | Panther added field with the source id |
| `p_source_label` | `string` | Panther added field with the source label |
| `p_any_ip_addresses` | `[string]` | Panther added field with collection of ip addresses associated with the row |
| `p_any_sha256_hashes` | `[string]` | Panther added field with collection of MD5 hashes associated with the row |
| `p_any_usernames` | `[string]` | Panther added field with collection of usernames associated with the row |

