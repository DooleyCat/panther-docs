# Okta Detections and Queries

## Integration

Panther supports Okta System Log as a native API puller. See the onboarding guide [here](../data-onboarding/saas-logs/okta.md).

The Okta System Log schema can be found under Analysis -&gt; Schema within the Panther UI or from the [Panther Analysis ](https://github.com/panther-labs/panther-analysis/blob/master/schemas/logs/okta/system_log.yml)repository on Github. 

## Native Detections

Panther has a number of detections specifically for Okta. These can all be found within the [Panther Analysis](https://github.com/panther-labs/panther-analysis) repository on Github. 

#### [Okta Admin Role Assigned](https://github.com/panther-labs/panther-analysis/blob/master/okta_rules/okta_admin_role_assigned.py) - A user has been granted administrative privileges in Okta=

#### [Okta API Key Created](https://github.com/panther-labs/panther-analysis/blob/master/okta_rules/okta_api_key_created.py) - A user created an API Key in Okta 

#### [Okta API Key Revoked](https://github.com/panther-labs/panther-analysis/blob/master/okta_rules/okta_api_key_revoked.py) - A user has revoked an API Key in Okta

#### [Geographically Improbable Okta Login](https://github.com/panther-labs/panther-analysis/blob/master/okta_rules/okta_geo_improbable_access.py) - A user has subsequent logins from two geographic locations that are very far apart

Have other Okta detections that can be used by other customers? Consider sharing detections back to the [Panther Analysis](https://github.com/panther-labs/panther-analysis) repository or work with your Customer Success team!  

## Custom Detections

#### Suspicious Behavior Reported

Description: A user has reported suspicious behavior from their account

```text
def rule(event):
    if event.get('eventtype') == 'user.account.report_suspicious_activity_by_enduser':
        return True
```

Below are some common functions and example `deep_get()` uses when writing custom detections for  Okta. Explanations on different event types can be found in the Okta [documentation](https://developer.okta.com/docs/reference/api/event-types/).

```text
#Okta has many event types that are listed here. You can begin your detection based on one of these eventtypes
#https://developer.okta.com/docs/reference/api/event-types/
event.get('eventtype')

#To access the city, state, lat, lon etc. 
deep_get(event, 'client', 'geographicalContext', 'city')
deep_get(event, 'client', 'geographicalContext', 'state')
deep_get(event, 'client', 'geographicalContext', 'country')
deep_get(event, 'client', 'geographicalContext', 'geolocation', 'lon')
deep_get(event, 'client', 'geographicalContext', 'geolocation', 'lat')

#Details on the source of the event
deep_get(event, 'client' 'device')
deep_get(event, 'client', 'ipAddress')
deep_get(event, 'client', 'userAgent')


deep_get(event, 'actor', 'alternateId')
deep_get(event, 'actor', 'displayName')

## Global helpers that may be useful with Okta

# within panther_base_helpers
def okta_alert_context(event: dict):
    """Returns common context for automation of Okta alerts"""
    return {
        "ips": event.get("p_any_ip_addresses", []),
        "actor": event.get("actor", ""),
        "target": event.get("target", ""),
        "client": event.get("client", ""),
    }
    
# within panther_base_helpers
def is_ip_in_network(ip_addr, networks):
    """Check that a given IP is within a list of IP ranges"""
    return any(ip_address(ip_addr) in ip_network(network) for network in networks)
```

## Queries

Below are a few queries to get started with investigating and learning your Okta events. These queries are written for Snowflake SQL syntax.

#### Top logins by user last 7 days

```text
-- Top logins by user last 7 days
SELECT actor:alternateId as actor, COUNT(*) as total
FROM panther_logs.public.okta_systemlog 
WHERE eventtype = 'user.authentication.sso' 
  and outcome:result = 'SUCCESS' 
  and p_occurs_since(7d)
GROUP BY actor
ORDER BY total desc
```

#### Logins by hour last 1 day

```text
-- Logins by hour last 1 day
SELECT  
  time_slice(p_event_time, 1, 'HOUR', 'START') as "start",
  time_slice(p_event_time, 1, 'HOUR', 'END') as "end",
  count(*) as "logins",
  count(distinct(actor:alternateId)) as "users"
FROM panther_logs.public.okta_systemlog 
WHERE eventtype = 'user.authentication.sso' 
  and outcome:result = 'SUCCESS' 
  and p_occurs_since(1d)
GROUP BY "start", "end"
ORDER BY "start" desc
```

#### Top applications last 7 days

```text
-- Top applications last 7 days
SELECT GET(target, 0):displayName as application, count(*) as total
FROM panther_logs.public.okta_systemlog 
WHERE eventtype = 'user.authentication.sso' 
  and p_occurs_since(7d)
GROUP BY Application
ORDER BY total desc
```

#### Top failing users last 7 days

```text
-- Top failing users last 7 days
SELECT actor:alternateId as actor, COUNT(*) as total
FROM panther_logs.public.okta_systemlog 
WHERE eventtype = 'user.session.start' 
  and outcome:result = 'FAILURE' 
  and outcome:reason = 'INVALID_CREDENTIALS'
  and p_occurs_since(7d)
GROUP BY actor
ORDER BY total desc
```

#### Login failures by reason last 7 days

```text
-- Login failures by reason
SELECT outcome:reason as reason, COUNT(*) as total
FROM panther_logs.public.okta_systemlog 
WHERE eventtype = 'user.session.start' 
  and outcome:result = 'FAILURE'
  and p_occurs_since(7d)
GROUP BY reason
ORDER BY total desc
```

#### Fake account login attempts last 7 days

```text
-- Fake account login attempts
SELECT actor:alternateId as actor, COUNT(*) as total
FROM panther_logs.public.okta_systemlog 
WHERE eventtype = 'user.session.start' and 
    outcome:result = 'FAILURE' and 
    outcome:reason = 'VERIFICATION_ERROR'
GROUP BY actor
ORDER BY total desc
```



