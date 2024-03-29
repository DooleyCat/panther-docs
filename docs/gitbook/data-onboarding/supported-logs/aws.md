# AWS

{% hint style="info" %}
Required fields are in **bold**.
{% endhint %}

## AWS.ALB

Application Load Balancer logs Layer 7 network logs for your application load balancer. Reference: [https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-access-logs.html](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-access-logs.html)

| Column | Type | Description |
| :--- | :--- | :--- |
| **`type`** | `string` | The type of request or connection. |
| **`timestamp`** | `timestamp` | The time when the load balancer generated a response to the client \(UTC\). For WebSockets, this is the time when the connection is closed. |
| `elb` | `string` | The resource ID of the load balancer. If you are parsing access log entries, note that resources IDs can contain forward slashes \(/\). |
| `clientIp` | `string` | The IP address of the requesting client. |
| `clientPort` | `bigint` | The port of the requesting client. |
| `targetIp` | `string` | The IP address of the target that processed this request. |
| `targetPort` | `bigint` | The port of the target that processed this request. |
| `requestProcessingTime` | `double` | The total time elapsed \(in seconds, with millisecond precision\) from the time the load balancer received the request until the time it sent it to a target. This value is set to -1 if the load balancer can't dispatch the request to a target. This can happen if the target closes the connection before the idle timeout or if the client sends a malformed request. This value can also be set to -1 if the registered target does not respond before the idle timeout. |
| `targetProcessingTime` | `double` | The total time elapsed \(in seconds, with millisecond precision\) from the time the load balancer sent the request to a target until the target started to send the response headers. This value is set to -1 if the load balancer can't dispatch the request to a target. This can happen if the target closes the connection before the idle timeout or if the client sends a malformed request. This value can also be set to -1 if the registered target does not respond before the idle timeout. |
| `responseProcessingTime` | `double` | The total time elapsed \(in seconds, with millisecond precision\) from the time the load balancer received the response header from the target until it started to send the response to the client. This includes both the queuing time at the load balancer and the connection acquisition time from the load balancer to the client. This value is set to -1 if the load balancer can't send the request to a target. This can happen if the target closes the connection before the idle timeout or if the client sends a malformed request. |
| **`elbStatusCode`** | `bigint` | The status code of the response from the load balancer. |
| `targetStatusCode` | `bigint` | The status code of the response from the target. This value is recorded only if a connection was established to the target and the target sent a response. |
| `receivedBytes` | `bigint` | The size of the request, in bytes, received from the client \(requester\). For HTTP requests, this includes the headers. For WebSockets, this is the total number of bytes received from the client on the connection. |
| `sentBytes` | `bigint` | The size of the response, in bytes, sent to the client \(requester\). For HTTP requests, this includes the headers. For WebSockets, this is the total number of bytes sent to the client on the connection. |
| `requestHttpMethod` | `string` | The HTTP method parsed from the request. |
| `requestUrl` | `string` | The HTTP URL parsed from the request. |
| `requestHttpVersion` | `string` | The HTTP version parsed from the request. |
| `userAgent` | `string` | A User-Agent string that identifies the client that originated the request. The string consists of one or more product identifiers, product\[/version\]. If the string is longer than 8 KB, it is truncated. |
| `sslCipher` | `string` | \[HTTPS listener\] The SSL cipher. This value is set to NULL if the listener is not an HTTPS listener. |
| `sslProtocol` | `string` | \[HTTPS listener\] The SSL protocol. This value is set to NULL if the listener is not an HTTPS listener. |
| `targetGroupArn` | `string` | The Amazon Resource Name \(ARN\) of the target group. |
| `traceId` | `string` | The contents of the X-Amzn-Trace-Id header. |
| `domainName` | `string` | \[HTTPS listener\] The SNI domain provided by the client during the TLS handshake. This value is set to NULL if the client doesn't support SNI or the domain doesn't match a certificate and the default certificate is presented to the client. |
| `chosenCertArn` | `string` | \[HTTPS listener\] The ARN of the certificate presented to the client. This value is set to session-reused if the session is reused. This value is set to NULL if the listener is not an HTTPS listener. |
| `matchedRulePriority` | `bigint` | The priority value of the rule that matched the request. If a rule matched, this is a value from 1 to 50,000. If no rule matched and the default action was taken, this value is set to 0. If an error occurs during rules evaluation, it is set to -1. For any other error, it is set to NULL. |
| `requestCreationTime` | `timestamp` | The time when the load balancer received the request from the client. |
| `actionsExecuted` | `[string]` | The actions taken when processing the request. This value is a comma-separated list that can include the values described in Actions Taken. If no action was taken, such as for a malformed request, this value is set to NULL. |
| `redirectUrl` | `string` | The URL of the redirect target for the location header of the HTTP response. If no redirect actions were taken, this value is set to NULL. |
| `errorReason` | `string` | The error reason code. If the request failed, this is one of the error codes described in Error Reason Codes. If the actions taken do not include an authenticate action or the target is not a Lambda function, this value is set to NULL. |
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
| `p_any_aws_account_ids` | `[string]` | Panther added field with collection of aws account ids associated with the row |
| `p_any_aws_instance_ids` | `[string]` | Panther added field with collection of aws instance ids associated with the row |
| `p_any_aws_arns` | `[string]` | Panther added field with collection of aws arns associated with the row |
| `p_any_aws_tags` | `[string]` | Panther added field with collection of aws tags associated with the row |

## AWS.AuroraMySQLAudit

AuroraMySQLAudit is an RDS Aurora audit log which contains context around database calls. Reference: [https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/AuroraMySQL.Auditing.html](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/AuroraMySQL.Auditing.html)

| Column | Type | Description |
| :--- | :--- | :--- |
| `timestamp` | `timestamp` | The timestamp for the logged event with microsecond precision \(UTC\). |
| `serverHost` | `string` | The name of the instance that the event is logged for. |
| `username` | `string` | The connected user name of the user. |
| `host` | `string` | The host that the user connected from. |
| `connectionId` | `bigint` | The connection ID number for the logged operation. |
| `queryId` | `bigint` | The query ID number, which can be used for finding the relational table events and related queries. For TABLE events, multiple lines are added. |
| **`operation`** | `string` | The recorded action type. Possible values are: CONNECT, QUERY, READ, WRITE, CREATE, ALTER, RENAME, and DROP. |
| `database` | `string` | The active database, as set by the USE command. |
| `object` | `string` | For QUERY events, this value indicates the executed query. For TABLE events, it indicates the table name. |
| `retCode` | `bigint` | The return code of the logged operation. |
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
| `p_any_aws_account_ids` | `[string]` | Panther added field with collection of aws account ids associated with the row |
| `p_any_aws_instance_ids` | `[string]` | Panther added field with collection of aws instance ids associated with the row |
| `p_any_aws_arns` | `[string]` | Panther added field with collection of aws arns associated with the row |
| `p_any_aws_tags` | `[string]` | Panther added field with collection of aws tags associated with the row |

## AWS.CloudTrail

AWSCloudTrail represents the content of a CloudTrail S3 object. Reference: [https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-event-reference.html](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-event-reference.html)

| Column | Type | Description |
| :--- | :--- | :--- |
| `additionalEventData` | `string` | Additional data about the event that was not part of the request or response. |
| `apiVersion` | `string` | Identifies the API version associated with the AwsApiCall eventType value. |
| **`awsRegion`** | `string` | The AWS region that the request was made to, such as us-east-2. |
| `errorCode` | `string` | The AWS service error if the request returns an error. |
| `errorMessage` | `string` | If the request returns an error, the description of the error. This message includes messages for authorization failures. CloudTrail captures the message logged by the service in its exception handling. |
| **`eventID`** | `string` | GUID generated by CloudTrail to uniquely identify each event. You can use this value to identify a single event. For example, you can use the ID as a primary key to retrieve log data from a searchable database. |
| **`eventName`** | `string` | The requested action, which is one of the actions in the API for that service. |
| **`eventSource`** | `string` | The service that the request was made to. This name is typically a short form of the service name without spaces plus .amazonaws.com. |
| **`eventTime`** | `timestamp` | The date and time the request was made, in coordinated universal time \(UTC\). |
| **`eventType`** | `string` | Identifies the type of event that generated the event record. This can be the one of the following values: AwsApiCall, AwsServiceEvent, AwsConsoleSignIn |
| **`eventVersion`** | `string` | The version of the log event format. |
| `managementEvent` | `boolean` | A Boolean value that identifies whether the event is a management event. managementEvent is shown in an event record if eventVersion is 1.06 or higher, and the event type is one of the following: AwsApiCall, AwsConsoleAction, AwsConsoleSignIn, AwsServiceEvent |
| `readOnly` | `boolean` | Identifies whether this operation is a read-only operation. |
| `recipientAccountId` | `string` | Represents the account ID that received this event. The recipientAccountID may be different from the CloudTrail userIdentity Element accountId. This can occur in cross-account resource access. |
| `requestID` | `string` | The value that identifies the request. The service being called generates this value. |
| `requestParameters` | `string` | The parameters, if any, that were sent with the request. These parameters are documented in the API reference documentation for the appropriate AWS service. |
| `resources` | `[{   "arn":string,   "accountId":string,   "type":string }]` | A list of resources accessed in the event. |
| `responseElements` | `string` | The response element for actions that make changes \(create, update, or delete actions\). If an action does not change state \(for example, a request to get or list objects\), this element is omitted. These actions are documented in the API reference documentation for the appropriate AWS service. |
| `serviceEventDetails` | `string` | Identifies the service event, including what triggered the event and the result. |
| `sharedEventID` | `string` | GUID generated by CloudTrail to uniquely identify CloudTrail events from the same AWS action that is sent to different AWS accounts. |
| **`sourceIPAddress`** | `string` | The IP address that the request was made from. For actions that originate from the service console, the address reported is for the underlying customer resource, not the console web server. For services in AWS, only the DNS name is displayed. |
| `userAgent` | `string` | The agent through which the request was made, such as the AWS Management Console, an AWS service, the AWS SDKs or the AWS CLI. |
| **`userIdentity`** | `{   "type":string,   "principalId":string,   "arn":string,   "accountId":string,   "accessKeyId":string,   "userName":string,   "sessionContext":{     "attributes":{       "mfaAuthenticated":string,       "creationDate":string },     "sessionIssuer":{       "type":string,       "principalId":string,       "arn":string,       "accountId":string,       "userName":string },     "webIdFederationData":{       "federatedProvider":string,       "attributes":string } },   "invokedBy":string,   "identityProvider":string }` | Information about the user that made a request. |
| `vpcEndpointId` | `string` | Identifies the VPC endpoint in which requests were made from a VPC to another AWS service, such as Amazon S3. |
| **`p_event_time`** | `timestamp` | Panther added standardized event time \(UTC\) |
| **`p_parse_time`** | `timestamp` | Panther added standardized log parse time \(UTC\) |
| **`p_log_type`** | `string` | Panther added field with type of log |
| **`p_row_id`** | `string` | Panther added field with unique id \(within table\) |
| `p_source_id` | `string` | Panther added field with the source id |
| `p_source_label` | `string` | Panther added field with the source label |
| `p_any_ip_addresses` | `[string]` | Panther added field with collection of ip addresses associated with the row |
| `p_any_domain_names` | `[string]` | Panther added field with collection of domain names associated with the row |
| `p_any_md5_hashes` | `[string]` | Panther added field with collection of SHA256 hashes of any algorithm associated with the row |
| `p_any_sha1_hashes` | `[string]` | Panther added field with collection of SHA1 hashes associated with the row |
| `p_any_sha256_hashes` | `[string]` | Panther added field with collection of MD5 hashes associated with the row |
| `p_any_trace_ids` | `[string]` | Panther added field with collection of context trace identifiers |
| `p_any_aws_account_ids` | `[string]` | Panther added field with collection of AWS account ids associated with the row |
| `p_any_aws_instance_ids` | `[string]` | Panther added field with collection of AWS instance ids associated with the row |
| `p_any_aws_arns` | `[string]` | Panther added field with collection of AWS ARNs associated with the row |
| `p_any_aws_tags` | `[string]` | Panther added field with collection of AWS Tags associated with the row |

## AWS.CloudTrailDigest

AWSCloudTrailDigest contains the names of the log files that were delivered to your Amazon S3 bucket during the last hour, the hash values for those log files, and the signature of the previous digest file. Reference: [https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-log-file-validation-digest-file-structure.html](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-log-file-validation-digest-file-structure.html)

| Column | Type | Description |
| :--- | :--- | :--- |
| **`awsAccountId`** | `string` | The AWS account ID for which the digest file has been delivered. |
| **`digestStartTime`** | `timestamp` | The starting UTC time range that the digest file covers, taking as a reference the time in which log files have been delivered by CloudTrail. |
| **`digestEndTime`** | `timestamp` | The ending UTC time range that the digest file covers, taking as a reference the time in which log files have been delivered by CloudTrail. |
| **`digestS3Bucket`** | `string` | The name of the Amazon S3 bucket to which the current digest file has been delivered. |
| **`digestS3Object`** | `string` | The Amazon S3 object key \(that is, the Amazon S3 bucket location\) of the current digest file. |
| `newestEventTime` | `timestamp` | The UTC time of the most recent event among all of the events in the log files in the digest. |
| `oldestEventTime` | `timestamp` | The UTC time of the oldest event among all of the events in the log files in the digest. |
| `previousDigestS3Bucket` | `string` | The Amazon S3 bucket to which the previous digest file was delivered. |
| `previousDigestS3Object` | `string` | The Amazon S3 object key \(that is, the Amazon S3 bucket location\) of the previous digest file. |
| `previousDigestHashValue` | `string` | The hexadecimal encoded hash value of the uncompressed contents of the previous digest file. |
| `previousDigestHashAlgorithm` | `string` | The name of the hash algorithm that was used to hash the previous digest file. |
| `previousDigestSignature` | `string` | The hexadecimal encoded signature of the previous digest file. |
| **`digestPublicKeyFingerprint`** | `string` | The hexadecimal encoded fingerprint of the public key that matches the private key used to sign this digest file. |
| **`digestSignatureAlgorithm`** | `string` | The algorithm used to sign the digest file. |
| **`logFiles`** | `[{   "s3Bucket":string,   "s3Object":string,   "hashValue":string,   "hashAlgorithm":string,   "newestEventTime":timestamp,   "oldestEventTime":timestamp }]` | Log files delivered in this digest |
| **`p_event_time`** | `timestamp` | Panther added standardized event time \(UTC\) |
| **`p_parse_time`** | `timestamp` | Panther added standardized log parse time \(UTC\) |
| **`p_log_type`** | `string` | Panther added field with type of log |
| **`p_row_id`** | `string` | Panther added field with unique id \(within table\) |
| `p_source_id` | `string` | Panther added field with the source id |
| `p_source_label` | `string` | Panther added field with the source label |
| `p_any_sha256_hashes` | `[string]` | Panther added field with collection of MD5 hashes associated with the row |
| `p_any_aws_account_ids` | `[string]` | Panther added field with collection of AWS account ids associated with the row |

## AWS.CloudTrailInsight

AWSCloudTrailInsight represents the content of a CloudTrail Insight event record S3 object. Reference: [https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-event-reference.html](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-event-reference.html)

| Column | Type | Description |
| :--- | :--- | :--- |
| **`eventVersion`** | `string` | The version of the log event format. |
| **`eventTime`** | `timestamp` | The date and time the request was made, in coordinated universal time \(UTC\). |
| **`awsRegion`** | `string` | The AWS region that the request was made to, such as us-east-2. |
| **`eventId`** | `string` | GUID generated by CloudTrail to uniquely identify each event. You can use this value to identify a single event. For example, you can use the ID as a primary key to retrieve log data from a searchable database. |
| **`eventType`** | `string` | Identifies the type of event that generated the event record. This can be the one of the following values: AwsApiCall, AwsServiceEvent, AwsConsoleSignIn |
| `recipientAccountId` | `string` | Represents the account ID that received this event. The recipientAccountID may be different from the CloudTrail userIdentity Element accountId. This can occur in cross-account resource access. |
| **`sharedEventId`** | `string` | A GUID that is generated by CloudTrail Insights to uniquely identify an Insights event. sharedEventID is common between the start and the end Insights events. |
| **`insightDetails`** | `{   "state":string,   "eventSource":string,   "eventName":string,   "insightType":string,   "insightContext":{     "statistics":{       "baseline":{         "average":double },       "insight":{         "average":double },       "insightDuration":float } } }` | Shows information about the underlying triggers of an Insights event, such as event source, statistics, API name, and whether the event is the start or end of the Insights event. |
| **`eventCategory`** | `string` | Shows the event category that is used in LookupEvents calls. In Insights events, the value is insight. |
| **`p_event_time`** | `timestamp` | Panther added standardized event time \(UTC\) |
| **`p_parse_time`** | `timestamp` | Panther added standardized log parse time \(UTC\) |
| **`p_log_type`** | `string` | Panther added field with type of log |
| **`p_row_id`** | `string` | Panther added field with unique id \(within table\) |
| `p_source_id` | `string` | Panther added field with the source id |
| `p_source_label` | `string` | Panther added field with the source label |
| `p_any_ip_addresses` | `[string]` | Panther added field with collection of ip addresses associated with the row |
| `p_any_domain_names` | `[string]` | Panther added field with collection of domain names associated with the row |
| `p_any_md5_hashes` | `[string]` | Panther added field with collection of SHA256 hashes of any algorithm associated with the row |
| `p_any_sha1_hashes` | `[string]` | Panther added field with collection of SHA1 hashes associated with the row |
| `p_any_sha256_hashes` | `[string]` | Panther added field with collection of MD5 hashes associated with the row |
| `p_any_trace_ids` | `[string]` | Panther added field with collection of context trace identifiers |
| `p_any_aws_account_ids` | `[string]` | Panther added field with collection of AWS account ids associated with the row |
| `p_any_aws_instance_ids` | `[string]` | Panther added field with collection of AWS instance ids associated with the row |
| `p_any_aws_arns` | `[string]` | Panther added field with collection of AWS ARNs associated with the row |
| `p_any_aws_tags` | `[string]` | Panther added field with collection of AWS Tags associated with the row |

## AWS.CloudWatchEvents

Amazon CloudWatch Events describe a change in Amazon Web Services \(AWS\) resources. Reference: [https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/CloudWatchEventsandEventPatterns.html](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/CloudWatchEventsandEventPatterns.html)

| Column | Type | Description |
| :--- | :--- | :--- |
| **`id`** | `string` | A unique value is generated for every event. This can be helpful in tracing events as they move through rules to targets, and are processed. |
| **`account`** | `string` | The 12-digit number identifying an AWS account. |
| **`source`** | `string` | Identifies the service that sourced the event. All events sourced from within AWS begin with 'aws'. Customer-generated events can have any value here, as long as it doesn't begin with 'aws'. We recommend the use of Java package-name style reverse domain-name strings. |
| **`resources`** | `[string]` | This JSON array contains ARNs that identify resources that are involved in the event. Inclusion of these ARNs is at the discretion of the service. For example, Amazon EC2 instance state-changes include Amazon EC2 instance ARNs, Auto Scaling events include ARNs for both instances and Auto Scaling groups, but API calls with AWS CloudTrail do not include resource ARNs. |
| **`region`** | `string` | Identifies the AWS region where the event originated. |
| **`detail-type`** | `string` | Identifies, in combination with the source field, the fields and values that appear in the detail field. |
| **`version`** | `string` | By default, this is set to 0 \(zero\) in all events. |
| **`time`** | `timestamp` | The event timestamp, which can be specified by the service originating the event. If the event spans a time interval, the service might choose to report the start time, so this value can be noticeably before the time the event is actually received. |
| **`detail`** | `string` | A JSON object, whose content is at the discretion of the service originating the event. The detail content in the example above is very simple, just two fields. AWS API call events have detail objects with around 50 fields nested several levels deep. |
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
| `p_any_aws_account_ids` | `[string]` | Panther added field with collection of aws account ids associated with the row |
| `p_any_aws_instance_ids` | `[string]` | Panther added field with collection of aws instance ids associated with the row |
| `p_any_aws_arns` | `[string]` | Panther added field with collection of aws arns associated with the row |
| `p_any_aws_tags` | `[string]` | Panther added field with collection of aws tags associated with the row |

## AWS.GuardDuty

Amazon GuardDuty is a threat detection service that continuously monitors for malicious activity and unauthorized behavior inside AWS Accounts. Reference: [https://docs.aws.amazon.com/guardduty/latest/ug/guardduty\_finding-format.html](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_finding-format.html)

| Column | Type | Description |
| :--- | :--- | :--- |
| **`schemaVersion`** | `string` | The schema format version of this record. |
| **`accountId`** | `string` | The ID of the AWS account in which the activity took place that prompted GuardDuty to generate this finding. |
| **`region`** | `string` | The AWS region in which the finding was generated. |
| **`partition`** | `string` | The AWS partition in which the finding was generated. |
| **`id`** | `string` | A unique identifier for the finding. |
| **`arn`** | `string` | A unique identifier formatted as an ARN for the finding. |
| **`type`** | `string` | A concise yet readable description of the potential security issue. |
| **`resource`** | `string` | The AWS resource against which the activity took place that prompted GuardDuty to generate this finding. |
| **`severity`** | `float` | The value of the severity can fall anywhere within the 0.1 to 8.9 range. |
| **`createdAt`** | `timestamp` | The initial creation time of the finding \(UTC\). |
| **`updatedAt`** | `timestamp` | The last update time of the finding \(UTC\). |
| **`title`** | `string` | A short description of the finding. |
| **`description`** | `string` | A long description of the finding. |
| **`service`** | `{   "additionalInfo":string,   "action":string,   "serviceName":string,   "detectorId":string,   "resourceRole":string,   "eventFirstSeen":timestamp,   "eventLastSeen":timestamp,   "archived":boolean,   "count":bigint }` | Additional information about the affected service. |
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
| `p_any_aws_account_ids` | `[string]` | Panther added field with collection of aws account ids associated with the row |
| `p_any_aws_instance_ids` | `[string]` | Panther added field with collection of aws instance ids associated with the row |
| `p_any_aws_arns` | `[string]` | Panther added field with collection of aws arns associated with the row |
| `p_any_aws_tags` | `[string]` | Panther added field with collection of aws tags associated with the row |

## AWS.S3ServerAccess

S3ServerAccess is an AWS S3 Access Log. Reference: [https://docs.aws.amazon.com/AmazonS3/latest/dev/LogFormat.html](https://docs.aws.amazon.com/AmazonS3/latest/dev/LogFormat.html)

| Column | Type | Description |
| :--- | :--- | :--- |
| **`bucketowner`** | `string` | The canonical user ID of the owner of the source bucket. The canonical user ID is another form of the AWS account ID. |
| `bucket` | `string` | The name of the bucket that the request was processed against. If the system receives a malformed request and cannot determine the bucket, the request will not appear in any server access log. |
| `time` | `timestamp` | The time at which the request was received \(UTC\). |
| `remoteip` | `string` | The apparent internet address of the requester. Intermediate proxies and firewalls might obscure the actual address of the machine making the request. |
| `requester` | `string` | The canonical user ID of the requester, or NULL for unauthenticated requests. If the requester was an IAM user, this field returns the requester's IAM user name along with the AWS root account that the IAM user belongs to. This identifier is the same one used for access control purposes. |
| `requestid` | `string` | A string generated by Amazon S3 to uniquely identify each request. |
| `operation` | `string` | The operation listed here is declared as SOAP.operation, REST.HTTP\_method.resource\_type, WEBSITE.HTTP\_method.resource\_type, or BATCH.DELETE.OBJECT. |
| `key` | `string` | The key part of the request, URL encoded, or NULL if the operation does not take a key parameter. |
| `requesturi` | `string` | The Request-URI part of the HTTP request message. |
| `httpstatus` | `bigint` | The numeric HTTP status code of the response. |
| `errorcode` | `string` | The Amazon S3 Error Code, or NULL if no error occurred. |
| `bytessent` | `bigint` | The number of response bytes sent, excluding HTTP protocol overhead, or NULL if zero. |
| `objectsize` | `bigint` | The total size of the object in question. |
| `totaltime` | `bigint` | The number of milliseconds the request was in flight from the server's perspective. This value is measured from the time your request is received to the time that the last byte of the response is sent. Measurements made from the client's perspective might be longer due to network latency. |
| `turnaroundtime` | `bigint` | The number of milliseconds that Amazon S3 spent processing your request. This value is measured from the time the last byte of your request was received until the time the first byte of the response was sent. |
| `referrer` | `string` | The value of the HTTP Referer header, if present. HTTP user-agents \(for example, browsers\) typically set this header to the URL of the linking or embedding page when making a request. |
| `useragent` | `string` | The value of the HTTP User-Agent header. |
| `versionid` | `string` | The version ID in the request, or NULL if the operation does not take a versionId parameter. |
| `hostid` | `string` | The x-amz-id-2 or Amazon S3 extended request ID. |
| `signatureversion` | `string` | The signature version, SigV2 or SigV4, that was used to authenticate the request or NULL for unauthenticated requests. |
| `ciphersuite` | `string` | The Secure Sockets Layer \(SSL\) cipher that was negotiated for HTTPS request or NULL for HTTP. |
| `authenticationtype` | `string` | The type of request authentication used, AuthHeader for authentication headers, QueryString for query string \(pre-signed URL\) or NULL for unauthenticated requests. |
| `hostheader` | `string` | The endpoint used to connect to Amazon S3. |
| `tlsVersion` | `string` | The Transport Layer Security \(TLS\) version negotiated by the client. The value is one of following: TLSv1, TLSv1.1, TLSv1.2; or NULL if TLS wasn't used. |
| `additionalFields` | `[string]` | The remaining columns in the record as an array. |
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
| `p_any_aws_account_ids` | `[string]` | Panther added field with collection of aws account ids associated with the row |
| `p_any_aws_instance_ids` | `[string]` | Panther added field with collection of aws instance ids associated with the row |
| `p_any_aws_arns` | `[string]` | Panther added field with collection of aws arns associated with the row |
| `p_any_aws_tags` | `[string]` | Panther added field with collection of aws tags associated with the row |

## AWS.VPCDns

DNS query logs of the queries that VPC DNS resolvers forward to Route 53. Reference: [https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-query-logs-format.html](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-query-logs-format.html)

| Column | Type | Description |
| :--- | :--- | :--- |
| **`version`** | `string` | The version number of the query log format. If we add fields to the log or change the format of existing fields, we'll increment this value. |
| **`account_id`** | `string` | The ID of the AWS account that created the VPC. |
| **`region`** | `string` | The AWS Region that you created the VPC in. |
| **`vpc_id`** | `string` | The ID of the VPC that the query originated in. |
| **`query_timestamp`** | `timestamp` | The date and time that the query was submitted, in ISO 8601 format and Coordinated Universal Time \(UTC\) |
| **`query_name`** | `string` | The domain name \(example.com\) or subdomain name \(www.example.com\) that was specified in the query. |
| **`query_type`** | `string` | Either the DNS record type that was specified in the request, or ANY. For information about the types that Route 53 supports. |
| **`query_class`** | `string` | The class of the query. |
| **`rcode`** | `string` | The DNS response code that Resolver returned in response to the DNS query. The response code indicates whether the query was valid or not. The most common response code is NOERROR, meaning that the query was valid. If the response is not valid, Resolver returns a response code that explains why not. For a list of possible response codes, see DNS RCODEs on the IANA website. |
| **`answers`** | `[{   "Rdata":string,   "Type":string,   "Class":string }]` | Answers to the query |
| **`srcaddr`** | `string` | The IP address of the instance that the query originated from. |
| **`srcport`** | `string` | The port on the instance that the query originated from. |
| **`transport`** | `string` | The protocol used to submit the DNS query. |
| **`srcids`** | `{   "instance":string,   "resolver-endpoint":string }` | The list of IDs of the sources the DNS query originated from or passed through. |
| **`p_event_time`** | `timestamp` | Panther added standardized event time \(UTC\) |
| **`p_parse_time`** | `timestamp` | Panther added standardized log parse time \(UTC\) |
| **`p_log_type`** | `string` | Panther added field with type of log |
| **`p_row_id`** | `string` | Panther added field with unique id \(within table\) |
| `p_source_id` | `string` | Panther added field with the source id |
| `p_source_label` | `string` | Panther added field with the source label |
| `p_any_ip_addresses` | `[string]` | Panther added field with collection of ip addresses associated with the row |
| `p_any_domain_names` | `[string]` | Panther added field with collection of domain names associated with the row |
| `p_any_aws_account_ids` | `[string]` | Panther added field with collection of AWS account ids associated with the row |
| `p_any_aws_instance_ids` | `[string]` | Panther added field with collection of AWS instance ids associated with the row |

## AWS.VPCFlow

VPCFlow is a VPC NetFlow log, which is a layer 3 representation of network traffic in EC2. Reference: [https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs-records-examples.html](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs-records-examples.html)

| Column | Type | Description |
| :--- | :--- | :--- |
| `version` | `bigint` | The VPC Flow Logs version. If you use the default format, the version is 2. If you specify a custom format, the version is 3. |
| `account` | `string` | The AWS account ID for the flow log. |
| `interfaceId` | `string` | The ID of the network interface for which the traffic is recorded. |
| `srcAddr` | `string` | The source address for incoming traffic, or the IPv4 or IPv6 address of the network interface for outgoing traffic on the network interface. The IPv4 address of the network interface is always its private IPv4 address. |
| `dstAddr` | `string` | The destination address for outgoing traffic, or the IPv4 or IPv6 address of the network interface for incoming traffic on the network interface. The IPv4 address of the network interface is always its private IPv4 address. |
| `srcPort` | `bigint` | The source port of the traffic. |
| `dstPort` | `bigint` | The destination port of the traffic. |
| `protocol` | `bigint` | The IANA protocol number of the traffic. |
| `packets` | `bigint` | The number of packets transferred during the flow. |
| `bytes` | `bigint` | The number of bytes transferred during the flow. |
| **`start`** | `timestamp` | The time of the start of the flow \(UTC\). |
| **`end`** | `timestamp` | The time of the end of the flow \(UTC\). |
| `action` | `string` | The action that is associated with the traffic. ACCEPT: The recorded traffic was permitted by the security groups or network ACLs. REJECT: The recorded traffic was not permitted by the security groups or network ACLs. |
| **`status`** | `string` | The logging status of the flow log. OK: Data is logging normally to the chosen destinations. NODATA: There was no network traffic to or from the network interface during the capture window. SKIPDATA: Some flow log records were skipped during the capture window. This may be because of an internal capacity constraint, or an internal error. |
| `vpcId` | `string` | The ID of the VPC that contains the network interface for which the traffic is recorded. |
| `subNetId` | `string` | The ID of the subnet that contains the network interface for which the traffic is recorded. |
| `instanceId` | `string` | The ID of the instance that's associated with network interface for which the traffic is recorded, if the instance is owned by you. Returns a '-' symbol for a requester-managed network interface; for example, the network interface for a NAT gateway. |
| `tcpFlags` | `bigint` | The bitmask value for the following TCP flags: SYN: 2, SYN-ACK: 18, FIN: 1, RST: 4. ACK is reported only when it's accompanied with SYN. TCP flags can be OR-ed during the aggregation interval. For short connections, the flags might be set on the same line in the flow log record, for example, 19 for SYN-ACK and FIN, and 3 for SYN and FIN. |
| `trafficType` | `string` | The type of traffic: IPv4, IPv6, or EFA. |
| `pktSrcAddr` | `string` | The packet-level \(original\) source IP address of the traffic. Use this field with the srcaddr field to distinguish between the IP address of an intermediate layer through which traffic flows, and the original source IP address of the traffic. For example, when traffic flows through a network interface for a NAT gateway, or where the IP address of a pod in Amazon EKS is different from the IP address of the network interface of the instance node on which the pod is running. |
| `pktDstAddr` | `string` | The packet-level \(original\) destination IP address for the traffic. Use this field with the dstaddr field to distinguish between the IP address of an intermediate layer through which traffic flows, and the final destination IP address of the traffic. For example, when traffic flows through a network interface for a NAT gateway, or where the IP address of a pod in Amazon EKS is different from the IP address of the network interface of the instance node on which the pod is running. |
| `pktSrcAwsService` | `string` | The name of the subset of IP address ranges for the pkt-srcaddr field, if the source IP address is for an AWS service. The possible values are: AMAZON \| AMAZON\_APPFLOW \| AMAZON\_CONNECT \| API\_GATEWAY \| CHIME\_MEETINGS \| CHIME\_VOICECONNECTOR \| CLOUD9 \| CLOUDFRONT \| CODEBUILD \| DYNAMODB \| EC2 \| EC2\_INSTANCE\_CONNECT \| GLOBALACCELERATOR \| KINESIS\_VIDEO\_STREAMS \| ROUTE53 \| ROUTE53\_HEALTHCHECKS \| S3 \| WORKSPACES\_GATEWAYS. |
| `pktDstAwsService` | `string` | The name of the subset of IP address ranges for the pkt-dstaddr field, if the destination IP address is for an AWS service. For a list of possible values, see the pkt-src-aws-service field. |
| `flowDirection` | `string` | The direction of the flow with respect to the interface where traffic is captured. The possible values are: ingress \| egress. |
| `trafficPath` | `tinyint` | The path that egress traffic takes to the destination. To determine whether the traffic is egress traffic, check the flow-direction field. The possible values are as follows. If none of the values apply, the field is set to -. If the network interface is attached to an instance based on the Nitro System, the possible values include 7 and 8 but not 2. With instances not based on the Nitro System \(for example, T2 and M4\), the possible values include 2 but not 7 or 8. 1 — Through another resource in the same VPC, 2 — Through an internet gateway or a gateway VPC endpoint, 3 — Through a virtual private gateway, 4 — Through an intra-region VPC peering connection, 5 — Through an inter-region VPC peering connection, 6 — Through a local gateway, 7 — Through a gateway VPC endpoint, 8 — Through an internet gateway |
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
| `p_any_aws_account_ids` | `[string]` | Panther added field with collection of aws account ids associated with the row |
| `p_any_aws_instance_ids` | `[string]` | Panther added field with collection of aws instance ids associated with the row |
| `p_any_aws_arns` | `[string]` | Panther added field with collection of aws arns associated with the row |
| `p_any_aws_tags` | `[string]` | Panther added field with collection of aws tags associated with the row |

## AWS.WAFWebACL

WAF Web ACL traffic information logs. Reference: [https://docs.aws.amazon.com/waf/latest/developerguide/logging.html](https://docs.aws.amazon.com/waf/latest/developerguide/logging.html)

| Column | Type | Description |
| :--- | :--- | :--- |
| **`action`** | `string` | The action applied by WAF. Possible values for a terminating rule: ALLOW and BLOCK. COUNT is not a valid value for a terminating rule. |
| `formatVersion` | `smallint` | The format version for the log. |
| **`httpRequest`** | `{   "args":string,   "clientIp":string,   "country":string,   "headers":[{     "name":string,     "value":string }],   "httpMethod":string,   "httpVersion":string,   "requestId":string,   "uri":string }` | The metadata about the request. |
| **`httpSourceId`** | `string` | The source ID. This field shows the ID of the associated resource. |
| `httpSourceName` | `string` | The source of the request. Possible values: CF for Amazon CloudFront, APIGW for Amazon API Gateway, ALB for Application Load Balancer, and APPSYNC for AWS AppSync. |
| `nonTerminatingMatchingRules` | `[{   "ruleId":string,   "action":string,   "ruleMatchDetails":[{     "conditionType":string,     "location":string,     "matchedData":[string] }] }]` | The list of non-terminating rules in the rule group that match the request. These are always COUNT rules \(non-terminating rules that match\). |
| `rateBasedRuleList` | `[{   "limitKey":string,   "limitValue":string,   "maxRateAllowed":bigint,   "rateBasedRuleId":string,   "rateBasedRuleName":string }]` | The list of rate-based rules that acted on the request. |
| `ruleGroupList` | `[{   "excludedRules":[{     "exclusionType":string,     "ruleId":string }],   "nonTerminatingMatchingRules":[{     "ruleId":string,     "action":string,     "ruleMatchDetails":[{       "conditionType":string,       "location":string,       "matchedData":[string] }] }],   "ruleGroupId":string,   "terminatingRule":{     "ruleId":string,     "action":string,     "ruleMatchDetails":[{       "conditionType":string,       "location":string,       "matchedData":[string] }] } }]` | The list of rule groups that acted on this request. In the preceding code example, there is only one. |
| `terminatingRuleId` | `string` | The ID of the rule that terminated the request. If nothing terminates the request, the value is Default\_Action. |
| `terminatingRuleMatchDetails` | `[{   "conditionType":string,   "location":string,   "matchedData":[string] }]` | Detailed information about the terminating rule that matched the request. A terminating rule has an action that ends the inspection process against a web request. Possible actions for a terminating rule are ALLOW and BLOCK. This is only populated for SQL injection and cross-site scripting \(XSS\) match rule statements. As with all rule statements that inspect for more than one thing, AWS WAF applies the action on the first match and stops inspecting the web request. A web request with a terminating action could contain other threats, in addition to the one reported in the log. |
| `terminatingRuleType` | `string` | The type of rule that terminated the request. Possible values: RATE\_BASED, REGULAR, GROUP, and MANAGED\_RULE\_GROUP. |
| **`timestamp`** | `timestamp` | The timestamp in milliseconds. |
| **`webaclId`** | `string` | The GUID of the web ACL. |
| **`p_event_time`** | `timestamp` | Panther added standardized event time \(UTC\) |
| **`p_parse_time`** | `timestamp` | Panther added standardized log parse time \(UTC\) |
| **`p_log_type`** | `string` | Panther added field with type of log |
| **`p_row_id`** | `string` | Panther added field with unique id \(within table\) |
| `p_source_id` | `string` | Panther added field with the source id |
| `p_source_label` | `string` | Panther added field with the source label |
| `p_any_ip_addresses` | `[string]` | Panther added field with collection of ip addresses associated with the row |
| `p_any_trace_ids` | `[string]` | Panther added field with collection of context trace identifiers |

