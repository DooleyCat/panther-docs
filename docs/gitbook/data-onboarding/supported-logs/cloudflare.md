# Cloudflare

{% hint style="info" %}
Required fields are in **bold**.
{% endhint %}

## Cloudflare.Firewall

Cloudflare Firewall logs. When selecting event fields on the Cloudflare UI, make sure you include the "Datetime" field as it is required by Panther. Reference: [https://developers.cloudflare.com/logs/log-fields\#firewall-events](https://developers.cloudflare.com/logs/log-fields#firewall-events)

| Column | Type | Description |
| :--- | :--- | :--- |
| `Action` | `string` | The code of the first-class action the Cloudflare Firewall took on this request |
| `ClientASN` | `bigint` | The ASN number of the visitor |
| `ClientASNDescription` | `string` | The ASN of the visitor as string |
| `ClientCountry` | `string` | Country from which request originated |
| `ClientIP` | `string` | The visitor's IP address \(IPv4 or IPv6\) |
| `ClientIPClass` | `string` | The classification of the visitor's IP address, possible values are: unknown \| clean \| badHost \| searchEngine \| whitelist \| greylist \| monitoringService \|securityScanner \| noRecord \| scan \| backupService \| mobilePlatform \| tor |
| `ClientRefererHost` | `string` | The referer host |
| `ClientRefererPath` | `string` | The referer path requested by visitor |
| `ClientRefererQuery` | `string` | The referer query-string was requested by the visitor |
| `ClientRefererScheme` | `string` | The referer url scheme requested by the visitor |
| `ClientRequestHost` | `string` | The HTTP hostname requested by the visitor |
| `ClientRequestMethod` | `string` | The HTTP method used by the visitor |
| `ClientRequestPath` | `string` | The path requested by visitor |
| `ClientRequestProtocol` | `string` | The version of HTTP protocol requested by the visitor |
| `ClientRequestQuery` | `string` | The query-string was requested by the visitor |
| `ClientRequestScheme` | `string` | The url scheme requested by the visitor |
| `ClientRequestUserAgent` | `string` | Visitor's user-agent string |
| **`Datetime`** | `timestamp` | The date and time the event occurred at the edge |
| `EdgeColoCode` | `string` | The airport code of the Cloudflare datacenter that served this request |
| `EdgeResponseStatus` | `smallint` | HTTP response status code returned to browser |
| `Kind` | `string` | The kind of event, currently only possible values are: firewall |
| `MatchIndex` | `bigint` | Rules match index in the chain |
| `Metadata` | `{   string:string }` | Additional product-specific information. Metadata is organized in key:value pairs. Key and Value formats can vary by Cloudflare security product and can change over time |
| `OriginResponseStatus` | `smallint` | HTTP origin response status code returned to browser |
| `OriginatorRayID` | `string` | The RayID of the request that issued the challenge/jschallenge |
| `RayID` | `string` | The RayID of the request |
| `RuleID` | `string` | The Cloudflare security product-specific RuleID triggered by this request |
| `Source` | `string` | The Cloudflare security product triggered by this request |
| **`p_event_time`** | `timestamp` | Panther added standardized event time \(UTC\) |
| **`p_parse_time`** | `timestamp` | Panther added standardized log parse time \(UTC\) |
| **`p_log_type`** | `string` | Panther added field with type of log |
| **`p_row_id`** | `string` | Panther added field with unique id \(within table\) |
| `p_source_id` | `string` | Panther added field with the source id |
| `p_source_label` | `string` | Panther added field with the source label |
| `p_any_ip_addresses` | `[string]` | Panther added field with collection of ip addresses associated with the row |
| `p_any_domain_names` | `[string]` | Panther added field with collection of domain names associated with the row |
| `p_any_trace_ids` | `[string]` | Panther added field with collection of context trace identifiers |

## Cloudflare.HttpRequest

Cloudflare http request logs. When selecting event fields on the Cloudflare UI, make sure you include the "EdgeStartTimestamp" field as it is required by Panther. Reference: [https://developers.cloudflare.com/logs/log-fields\#http-requests](https://developers.cloudflare.com/logs/log-fields#http-requests)

| Column | Type | Description |
| :--- | :--- | :--- |
| `BotScore` | `bigint` | Cloudflare Bot Score \(available for Bot Management customers; please contact your account team to enable\) |
| `BotScoreSrc` | `string` | Underlying detection engine or source on where a Bot Score is calculated. Possible values are Not Computed \| Heuristics \| Machine Learning \| Behavioral Analysis \| Verified Bot |
| `CacheCacheStatus` | `string` | unknown \| miss \| expired \| updating \| stale \| hit \| ignored \| bypass \| revalidated |
| `CacheResponseBytes` | `bigint` | Number of bytes returned by the cache |
| `CacheResponseStatus` | `smallint` | HTTP status code returned by the cache to the edge; all requests \(including non-cacheable ones\) go through the cache; also see CacheStatus field |
| `CacheTieredFill` | `boolean` | Tiered Cache was used to serve this request |
| `ClientASN` | `bigint` | Client AS number |
| `ClientCountry` | `string` | Country of the client IP address |
| `ClientDeviceType` | `string` | Client device type |
| `ClientIP` | `string` | IP address of the client |
| `ClientIPClass` | `string` | unknown \| clean \| badHost \| searchEngine \| whitelist \| greylist \| monitoringService \| securityScanner \| noRecord \| scan \|backupService \| mobilePlatform \| tor |
| `ClientRequestBytes` | `bigint` | Number of bytes in the client request |
| `ClientRequestHost` | `string` | Host requested by the client |
| `ClientRequestMethod` | `string` | HTTP method of client request |
| `ClientRequestPath` | `string` | URI path requested by the client |
| `ClientRequestProtocol` | `string` | HTTP protocol of client request |
| `ClientRequestReferer` | `string` | HTTP request referrer |
| `ClientRequestURI` | `string` | URI requested by the client |
| `ClientRequestUserAgent` | `string` | User agent reported by the client |
| `ClientSSLProtocol` | `string` | Client SSL \(TLS\) protocol |
| `ClientSrcPort` | `int` | Client source port |
| `ClientXRequestedWith` | `string` | X-Requested-With HTTP header |
| `EdgeColoCode` | `string` | IATA airport code of data center that received the request |
| `EdgeColoID` | `bigint` | Cloudflare edge colo id |
| `EdgeEndTimestamp` | `timestamp` | Timestamp at which the edge finished sending response to the client |
| `EdgePathingOp` | `string` | Indicates what type of response was issued for this request \(unknown = no specific action\) |
| `EdgePathingSrc` | `string` | Details how the request was classified based on security checks \(unknown = no specific classification\) |
| `EdgePathingStatus` | `string` | Indicates what data was used to determine the handling of this request \(unknown = no data\) |
| `EdgeRateLimitAction` | `string` | The action taken by the blocking rule; empty if no action taken |
| `EdgeRateLimitID` | `string` | The internal rule ID of the rate-limiting rule that triggered a block \(ban\) or simulate action. 0 if no action taken |
| `EdgeRequestHost` | `string` | Host header on the request from the edge to the origin |
| `EdgeResponseBytes` | `bigint` | Number of bytes returned by the edge to the client |
| `EdgeResponseCompressionRatio` | `float` | Edge response compression ratio |
| `EdgeResponseContentType` | `string` | Edge response Content-Type header value |
| `EdgeResponseStatus` | `smallint` | HTTP status code returned by Cloudflare to the client |
| `EdgeServerIP` | `string` | IP of the edge server making a request to the origin |
| **`EdgeStartTimestamp`** | `timestamp` | Timestamp at which the edge received request from the client |
| `FirewallMatchesActions` | `[string]` | Array of actions the Cloudflare firewall products performed on this request. The individual firewall products associated with this action be found in FirewallMatchesSources and their respective RuleIds can be found in FirewallMatchesRuleIDs. The length of the array is the same as FirewallMatchesRuleIDs and FirewallMatchesSources. Possible actions are allow \| log \| simulate \| drop \| challenge \| jschallenge \| connectionClose \| challengeSolved \| challengeFailed \| challengeBypassed \| jschallengeSolved \| jschallengeFailed \| jschallengeBypassed \| bypass |
| `FirewallMatchesRuleIDs` | `[string]` | Array of RuleIDs of the firewall product that has matched the request. The firewall product associated with the RuleID can be found in FirewallMatchesSources. The length of the array is the same as FirewallMatchesActions and FirewallMatchesSources. |
| `FirewallMatchesSources` | `[string]` | The firewall products that matched the request. The same product can appear multiple times, which indicates different rules or actions that were activated. The RuleIDs can be found in FirewallMatchesRuleIDs, the actions can be found in FirewallMatchesActions. The length of the array is the same as FirewallMatchesRuleIDs and FirewallMatchesActions. Possible sources are asn \| country \| ip \| ipRange \| securityLevel \| zoneLockdown \| waf \| firewallRules \| uaBlock \| rateLimit \|bic \| hot \| l7ddos \| sanitycheck \| protect |
| `OriginIP` | `string` | IP of the origin server |
| `OriginResponseBytes` | `bigint` | Number of bytes returned by the origin server |
| `OriginResponseHTTPExpires` | `timestamp` | Value of the origin 'expires' header in RFC1123 format |
| `OriginResponseHTTPLastModified` | `timestamp` | Value of the origin 'last-modified' header in RFC1123 format |
| `OriginResponseStatus` | `smallint` | Status returned by the origin server |
| `OriginResponseTime` | `bigint` | Number of nanoseconds it took the origin to return the response to edge |
| `OriginSSLProtocol` | `string` | SSL \(TLS\) protocol used to connect to the origin |
| `ParentRayID` | `string` | Ray ID of the parent request if this request was made using a Worker script |
| `RayID` | `string` | ID of the request |
| `SecurityLevel` | `string` | The security level configured at the time of this request. This is used to determine the sensitivity of the IP Reputation system |
| `WAFAction` | `string` | Action taken by the WAF, if triggered |
| `WAFFlags` | `string` | Additional configuration flags: simulate \(0x1\) \| null |
| `WAFMatchedVar` | `string` | The full name of the most-recently matched variable |
| `WAFProfile` | `string` | low \| med \| high |
| `WAFRuleID` | `string` | ID of the applied WAF rule |
| `WAFRuleMessage` | `string` | Rule message associated with the triggered rule |
| `WorkerCPUTime` | `bigint` | Amount of time in microseconds spent executing a worker, if any |
| `WorkerStatus` | `string` | Status returned from worker daemon |
| `WorkerSubrequest` | `boolean` | Whether or not this request was a worker subrequest |
| `WorkerSubrequestCount` | `bigint` | Number of subrequests issued by a worker when handling this request |
| `ZoneID` | `bigint` | Internal zone ID |
| **`p_event_time`** | `timestamp` | Panther added standardized event time \(UTC\) |
| **`p_parse_time`** | `timestamp` | Panther added standardized log parse time \(UTC\) |
| **`p_log_type`** | `string` | Panther added field with type of log |
| **`p_row_id`** | `string` | Panther added field with unique id \(within table\) |
| `p_source_id` | `string` | Panther added field with the source id |
| `p_source_label` | `string` | Panther added field with the source label |
| `p_any_ip_addresses` | `[string]` | Panther added field with collection of ip addresses associated with the row |
| `p_any_domain_names` | `[string]` | Panther added field with collection of domain names associated with the row |
| `p_any_trace_ids` | `[string]` | Panther added field with collection of context trace identifiers |

## Cloudflare.Spectrum

Cloudflare Spectrum logs. When selecting event fields on the Cloudflare UI, make sure you include the "Timestamp" field as it is required by Panther. Reference: [https://developers.cloudflare.com/logs/log-fields\#spectrum-events](https://developers.cloudflare.com/logs/log-fields#spectrum-events)

| Column | Type | Description |
| :--- | :--- | :--- |
| `Application` | `string` | The unique public ID of the application on which the event occurred |
| `ClientASN` | `bigint` | Client AS number |
| `ClientBytes` | `bigint` | The number of bytes read from the client by the Spectrum service |
| `ClientCountry` | `string` | Country of the client IP address |
| `ClientIP` | `string` | IP address of the client |
| `ClientMatchedIpFirewall` | `string` | Whether the connection matched any IP Firewall rules; UNKNOWN \| ALLOW \| BLOCK\_ERROR \| BLOCK\_IP \| BLOCK\_COUNTRY \| BLOCK\_ASN \| WHITELIST\_IP \|WHITELIST\_COUNTRY \| WHITELIST\_ASN |
| `ClientPort` | `int` | Client port |
| `ClientProto` | `string` | Transport protocol used by client; tcp \| udp \| unix |
| `ClientTcpRtt` | `bigint` | The TCP round-trip time in nanoseconds between the client and Spectrum |
| `ClientTlsCipher` | `string` | The cipher negotiated between the client and Spectrum |
| `ClientTlsClientHelloServerName` | `string` | The server name in the Client Hello message from client to Spectrum |
| `ClientTlsProtocol` | `string` | The TLS version negotiated between the client and Spectrum; unknown \| none \| SSLv3 \| TLSv1 \| TLSv1.1 \| TLSv1.2 \| TLSv1.3 |
| `ClientTlsStatus` | `string` | Indicates state of TLS session from the client to Spectrum; UNKNOWN \| OK \| INTERNAL\_ERROR \| INVALID\_CONFIG \| INVALID\_SNI \| HANDSHAKE\_FAILED \| KEYLESS\_RPC |
| `ColoCode` | `string` | IATA airport code of data center that received the request |
| `ConnectTimestamp` | `timestamp` | Timestamp at which both legs of the connection \(client/edge, edge/origin or nexthop\) were established |
| `DisconnectTimestamp` | `timestamp` | Timestamp at which the connection was closed |
| `Event` | `string` | connect \| disconnect \| clientFiltered \| tlsError \| resolveOrigin \| originError |
| `IpFirewall` | `boolean` | Whether IP Firewall was enabled at time of connection |
| `OriginBytes` | `bigint` | The number of bytes read from the origin by Spectrum |
| `OriginIP` | `string` | Origin IP address |
| `OriginPort` | `int` | Origin port |
| `OriginProto` | `string` | Transport protocol used by origin; tcp \| udp \| unix |
| `OriginTcpRtt` | `bigint` | The TCP round-trip time in nanoseconds between Spectrum and the origin |
| `OriginTlsCipher` | `string` | The cipher negotiated between Spectrum and the origin |
| `OriginTlsFingerprint` | `string` | SHA256 hash of origin certificate |
| `OriginTlsMode` | `string` | If and how the upstream connection is encrypted; unknown \| off \| flexible \| full \| strict |
| `OriginTlsProtocol` | `string` | The TLS version negotiated between Spectrum and the origin; unknown \| none \| SSLv3 \| TLSv1 \| TLSv1.1 \| TLSv1.2 \| TLSv1.3 |
| `OriginTlsStatus` | `string` | The state of the TLS session from Spectrum to the origin; UNKNOWN \| OK \| INTERNAL\_ERROR \| INVALID\_CONFIG \| INVALID\_SNI \| HANDSHAKE\_FAILED \| KEYLESS\_RPC |
| `ProxyProtocol` | `string` | Which form of proxy protocol is applied to the given connection; off \| v1 \| v2 \| simple |
| `Status` | `bigint` | A code indicating reason for connection closure |
| **`Timestamp`** | `timestamp` | Timestamp at which the event took place |
| **`p_event_time`** | `timestamp` | Panther added standardized event time \(UTC\) |
| **`p_parse_time`** | `timestamp` | Panther added standardized log parse time \(UTC\) |
| **`p_log_type`** | `string` | Panther added field with type of log |
| **`p_row_id`** | `string` | Panther added field with unique id \(within table\) |
| `p_source_id` | `string` | Panther added field with the source id |
| `p_source_label` | `string` | Panther added field with the source label |
| `p_any_ip_addresses` | `[string]` | Panther added field with collection of ip addresses associated with the row |

