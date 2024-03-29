# Lookup Tables (BETA)

{% hint style="info" %}
This feature is available in version 1.27 and newer.

Lookup Tables are currently in beta. This means:&#x20;

* We would greatly appreciate feedback such as bug reports and feature requests.
* The feature will gain new functionality in future versions of Panther.&#x20;
* The UI is likely to significantly evolve over time.
{% endhint %}

### Overview

Lookup Tables allow you to add important context to your detections and alerts for improved investigation workflows. Use Lookup Tables to enhance alerts with identity/asset information, vulnerability context, network maps, and more.



### Configuring a Lookup Table

You can populate your Lookup Table data using the following methods:

#### Import via File Upload

This option is best for data that is relatively static, such as information about AWS accounts or corporate subnets.&#x20;

For instructions, please see the documentation: [Import via File Upload](file-upload.md).

#### Sync Data from an S3 Source

This option is best for a larger amount of data that updates more frequently from an S3 bucket. Any changes in the S3 bucket will sync to Panther.

For instructions, please see the documentation: [Sync data from an S3 Source](s3-source.md).



### Examples

#### Translating 1Password UUIDs into human readable names

Please see our guide about using Lookup Tables to translate 1Password's Universally Unique Identifier (UUID) values into human readable names: [Using Lookup Tables: 1Password UUIDs](https://docs.runpanther.io/guides/using-lookup-tables-1password-uuids).

#### Lookup Table using CIDR matching

You can write detections that consider the traffic logs from company IP space (e.g. VPNs and hosted systems) differently from others logs originating from public IP space: [Lookup Table example using CIDR matching](file-upload.md#example-using-cidr-matching).
