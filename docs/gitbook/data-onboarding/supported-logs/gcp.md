# GCP

{% hint style="info" %}
Required fields are in **bold**.
{% endhint %}

## GCP.AuditLog

Cloud Audit Logs maintains three audit logs for each Google Cloud project, folder, and organization: Admin Activity, Data Access, and System Event. Google Cloud services write audit log entries to these logs to help you answer the questions of "who did what, where, and when?" within your Google Cloud resources.

Panther Enterprise Only

Reference: [https://cloud.google.com/logging/docs/audit](https://cloud.google.com/logging/docs/audit)

| Column | Type | Description |
| :--- | :--- | :--- |
| **`logName`** | `string` | The resource name of the log to which this log entry belongs. |
| `severity` | `string` | The severity of the log entry. The default value is LogSeverity.DEFAULT. |
| `insertId` | `string` | A unique identifier for the log entry. |
| `resource` | `{   "type":string,   "labels":{     string:string } }` | The monitored resource that produced this log entry. |
| `timestamp` | `timestamp` | The time the event described by the log entry occurred. |
| **`receiveTimestamp`** | `timestamp` | The time the log entry was received by Logging. |
| `labels` | `{   string:string }` | A set of user-defined \(key, value\) data that provides additional information about the log entry. |
| `operation` | `{   "id":string,   "producer":string,   "first":boolean,   "last":boolean }` | Information about an operation associated with the log entry, if applicable. |
| `trace` | `string` | Resource name of the trace associated with the log entry, if any. |
| `httpRequest` | `{   "requestMethod":string,   "requestURL":string,   "requestSize":bigint,   "status":smallint,   "responseSize":bigint,   "userAgent":string,   "remoteIP":string,   "serverIP":string,   "referer":string,   "latency":string,   "cacheLookup":boolean,   "cacheHit":boolean,   "cacheValidatedWithOriginServer":boolean,   "cacheFillBytes":bigint,   "protocol":string }` | Information about the HTTP request associated with this log entry, if applicable. |
| `spanId` | `string` | The span ID within the trace associated with the log entry. |
| `traceSampled` | `boolean` | The sampling decision of the trace associated with the log entry. |
| `sourceLocation` | `{   "file":string,   "line":bigint,   "function":string }` | Source code location information associated with the log entry, if any. |
| **`protoPayload`** | `{   "at_sign_type":string,   "serviceName":string,   "methodName":string,   "resourceName":string,   "numResponseItems":bigint,   "status":{     "code":int,     "message":string,     "details":string },   "authenticationInfo":{     "principalSubject":string,     "serviceAccountKeyName":string,     "principalEmail":string,     "authoritySelector":string,     "thirdPartyPrincipal":string,     "serviceAccountDelegationInfo":[{       "firstPartyPrincipal":{         "principalEmail":string,         "serviceMetadata":string },       "thirdPartyPrincipal":{         "thirdPartyClaims":string } }] },   "authorizationInfo":[{     "resource":string,     "permission":string,     "granted":boolean,     "resourceAttributes":{       "service":string,       "name":string,       "type":string,       "labels":string,       "uid":string } }],   "requestMetadata":{     "callerIP":string,     "callerSuppliedUserAgent":string,     "callerNetwork":string,     "requestAttributes":string,     "destinationAttributes":string },   "request":string,   "response":string,   "serviceData":string,   "metadata":string }` | The AuditLog payload |
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

