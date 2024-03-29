# OSSEC

{% hint style="info" %}
Required fields are in **bold**.
{% endhint %}

## OSSEC.EventInfo

OSSEC EventInfo alert parser. Currently only JSON output is supported. Reference: [https://www.ossec.net/docs/docs/formats/alerts.html](https://www.ossec.net/docs/docs/formats/alerts.html)

| Column | Type | Description |
| :--- | :--- | :--- |
| **`id`** | `string` | Unique id of the event. |
| **`rule`** | `{   "comment":string,   "group":string,   "level":bigint,   "sidid":bigint,   "CIS":[string],   "cve":string,   "firedtimes":bigint,   "frequency":bigint,   "groups":[string],   "info":string,   "PCI_DSS":[string] }` | Information about the rule that created the event. |
| **`TimeStamp`** | `timestamp` | Timestamp in UTC. |
| **`location`** | `string` | Source of the event \(filename, command, etc\). |
| **`hostname`** | `string` | Hostname of the host that created the event. |
| **`full_log`** | `string` | The full captured log of the event. |
| `action` | `string` | The event action \(drop, deny, accept, etc\). |
| `agentip` | `string` | The IP address of an agent extracted from the hostname. |
| `agent_name` | `string` | The name of an agent extracted from the hostname. |
| `command` | `string` | The command extracted by the decoder. |
| `data` | `string` | Additional data extracted by the decoder. For example a filename. |
| `decoder` | `string` | The name of the decoder used to parse the logs. |
| `decoder_desc` | `{   "accumulate":bigint,   "fts":bigint,   "ftscomment":string,   "name":string,   "parent":string }` | Information about the decoder used to parse the logs. |
| `decoder_parent` | `string` | In the case of a nested decoder, the name of it's parent. |
| `dstgeoip` | `string` | GeoIP location information about the destination IP address. |
| `dstip` | `string` | The destination IP address. |
| `dstport` | `string` | The destination port. |
| `dstuser` | `string` | The destination \(target\) username. |
| `logfile` | `string` | The source log file that was decoded to generate the event. |
| `previous_output` | `string` | The full captured log of the previous event. |
| `program_name` | `string` | The executable name extracted from the log by the decoder used to match a rule. |
| `protocol` | `string` | The protocol \(ip, tcp, udp, etc\) extracted by the decoder. |
| `srcgeoip` | `string` | GeoIP location information about the source IP address. |
| `srcip` | `string` | The source IP address. |
| `srcport` | `string` | The source port. |
| `srcuser` | `string` | The source username. |
| `status` | `string` | Event status \(success, failure, etc\). |
| `SyscheckFile` | `{   "gowner_after":string,   "gowner_before":string,   "md5_after":string,   "md5_before":string,   "owner_after":string,   "owner_before":string,   "path":string,   "perm_after":bigint,   "perm_before":bigint,   "sha1_after":string,   "sha1_before":string }` | Information about a file integrity check. |
| `systemname` | `string` | The system name extracted by the decoder. |
| `url` | `string` | URL of the event. |
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

