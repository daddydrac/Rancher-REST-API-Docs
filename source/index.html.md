---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Welcome to the Rancher API Docs

Welcome to the Rancher API docs.

This example API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Launching Kubernetes

## Custom Cluster

```shell
Host: ec2-35-160-22-186.us-west-2.compute.amazonaws.com
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:72.0) Gecko/20100101 Firefox/72.0
Accept: application/json
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
content-type: application/json
x-api-action-links: actionLinks
x-api-no-challenge: true
x-api-csrf: ecf5380918
Content-Length: 1192
Origin: https://ec2-35-160-22-186.us-west-2.compute.amazonaws.com
Connection: keep-alive
Referer: https://ec2-35-160-22-186.us-west-2.compute.amazonaws.com/g/clusters/add/launch/custom
Cookie: CSRF=ecf5380918; hibext_instdsigdipv2=1; R_SESS=token-kgvjq:jd962xfqlpcxx56mcpjmvmhxg6gvr6548s9h8c62bqxzzzbq8sfvhz; R_USERNAME=admin
{
  "dockerRootDir": "/var/lib/docker",
  "enableClusterAlerting": false,
  "enableClusterMonitoring": false,
  "enableNetworkPolicy": false,
  "windowsPreferedCluster": false,
  "type": "cluster",
  "rancherKubernetesEngineConfig": {
    "addonJobTimeout": 30,
    "ignoreDockerVersion": true,
    "sshAgentAuth": false,
    "type": "rancherKubernetesEngineConfig",
    "kubernetesVersion": "v1.17.0-rancher1-2",
    "authentication": {
      "strategy": "x509",
      "type": "authnConfig"
    },
    "network": {
      "mtu": 0,
      "plugin": "canal",
      "type": "networkConfig",
      "options": {
        "flannel_backend_type": "vxlan"
      }
    },
    "ingress": {
      "provider": "nginx",
      "type": "ingressConfig"
    },
    "monitoring": {
      "provider": "metrics-server",
      "type": "monitoringConfig"
    },
    "services": {
      "type": "rkeConfigServices",
      "kubeApi": {
        "alwaysPullImages": false,
        "podSecurityPolicy": false,
        "serviceNodePortRange": "30000-32767",
        "type": "kubeAPIService"
      },
      "etcd": {
        "creation": "12h",
        "extraArgs": {
          "heartbeat-interval": 500,
          "election-timeout": 5000
        },
        "gid": 0,
        "retention": "72h",
        "snapshot": false,
        "uid": 0,
        "type": "etcdService",
        "backupConfig": {
          "enabled": true,
          "intervalHours": 12,
          "retention": 6,
          "safeTimestamp": false,
          "type": "backupConfig"
        }
      }
    }
  },
  "localClusterAuthEndpoint": {
    "enabled": true,
    "type": "localClusterAuthEndpoint"
  },
  "labels": {},
  "name": "new-custom-cluster"
}
```

When you create a custom cluster, Rancher uses RKE (the Rancher Kubernetes Engine) to create a Kubernetes cluster in on-premise bare-metal servers, on-premise virtual machines, or in any node hosted by an infrastructure provider.

The default values nested in `rancherKubernetesEngineConfig` are the default values for clusters provisioned with RKE.

To use this option you’ll need access to servers you intend to use in your Kubernetes cluster. Provision each server according to the requirements, which includes some hardware specifications and Docker. After you install Docker on each server, run the command provided in the Rancher UI to turn each server into a Kubernetes node.

### HTTP Request

`POST RANCHER_SERVER_URL/v3/cluster?_replace=true`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
dockerRootDir | /var/lib/docker | ?
enableClusterAlerting | false | ?
enableClusterMonitoring | false | ?
enableNetworkPolicy | false | ?
windowsPreferedCluster | false | ?
type | cluster | ?
rancherKubernetesEngineConfig | RKE defaults | RKE config
addonJobTimeout | 30 | ?
ignoreDockerVersion | true | ?
sshAgentAuth | false | ?
type | "rancherKubernetesEngineConfig" | ?
kubernetesVersion | "v1.17.0-rancher1-2" | ?
authentication | ? | ?
authentication.strategy | "x509" | ?
authentication.type | "authnConfig" | ?
network | object | ?
network.mtu | 0 | ?
network.plugin | "canal" | ?
network.type | "networkConfig" | ?
network.options | {flannel_backend_type: "vxlan"} | ?
ingress | object | ?
ingress.provider | "nginx" | ?
ingress.type | "ingressConfig" | ?
monitoring | object | ?
monitoring.provider | "metrics-server" | ?
monitoring.type | "monitoringConfig" | ?
services | object | ?
services.type | "rkeConfigServices" | ?
services.kubeApi | object | ?
kubeApi.alwaysPullImages | false | ?
kubeApi.podSecurityPolicy | false | ?
kubeApi.serviceNodePortRange | "30000-32767" | ?
kubeApi.type | "kubeAPIService" | ?
services.etcd | object | ?
etcd.creation | "12h" | ?
etcd.extraArgs | object | ?
extraArgs.heartbeat-interval | 500 | ?
extraArgs.election-timeout | 5000 | ?
etcd.gid | 0 | ?
etcd.retention | "72h" | ?
etcd.snapshot | false | ?
etcd.uid | 0 | ?
etcd.type | "etcdService" | ?
backupConfig | object | ?
backupConfig.enabled | true | ?
backupConfig.intervalHours | 12 | ?
backupConfig.retention | 6 | ?
backupConfig.safeTimeStamp | false | ?
backupConfig.type | "backupConfig" | ?
localClusterAuthEndpoint | object | ?
localClusterAuthEndpoint.enabled | true | ?
localClusterAuthEndpoint.type | "localClusterAuthEndpoint" | ?
labels | {} | ?
name | No default, required field | Cluster name

# Node Templates

## Cloning a Node Template
```shell
Host: RANCHER_SERVER_URL
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:72.0) Gecko/20100101 Firefox/72.0
Accept: application/json
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
content-type: application/json
x-api-action-links: actionLinks
x-api-no-challenge: true
x-api-csrf: ecf5380918
Content-Length: 1238
Origin: RANCHER_SERVER_URL
Connection: keep-alive
Referer: RANCHER_SERVER_URL/n/node-templates
Cookie: CSRF=ecf5380918; hibext_instdsigdipv2=1; R_SESS=token-kgvjq:jd962xfqlpcxx56mcpjmvmhxg6gvr6548s9h8c62bqxzzzbq8sfvhz; R_USERNAME=admin
{
  "useInternalIpAddress": true,
  "amazonec2Config": {
    "accessKey": "",
    "ami": "",
    "blockDurationMinutes": "0",
    "deviceName": "/dev/sda1",
    "endpoint": "",
    "iamInstanceProfile": "",
    "insecureTransport": false,
    "instanceType": "t2.medium",
    "keypairName": "",
    "monitoring": false,
    "privateAddressOnly": false,
    "region": "us-west-2",
    "requestSpotInstance": false,
    "retries": "5",
    "rootSize": "16",
    "securityGroup": [
      "rancher-nodes"
    ],
    "securityGroupReadonly": false,
    "sessionToken": "",
    "spotPrice": "0.50",
    "sshUser": "ubuntu",
    "subnetId": "subnet-a27955e9",
    "tags": "",
    "useEbsOptimizedInstance": false,
    "usePrivateAddress": false,
    "userdata": "",
    "volumeType": "gp2",
    "vpcId": "vpc-2745f35f",
    "zone": "b"
  },
  "annotations": {
    "ownerBindingsCreated": "true"
  },
  "baseType": "nodeTemplate",
  "cloudCredentialId": "cattle-global-data:cc-djc44",
  "created": "2020-01-15T19:56:16Z",
  "createdTS": 1579118176000,
  "creatorId": "user-lv6bp",
  "driver": "amazonec2",
  "engineInstallURL": "https://releases.rancher.com/install-docker/19.03.sh",
  "engineRegistryMirror": null,
  "labels": {
    "cattle.io/creator": "norman"
  },
  "principalId": "local://user-lv6bp",
  "state": "active",
  "transitioning": "no",
  "transitioningMessage": "",
  "type": "nodeTemplate",
  "displayLocation": "us-west-2b",
  "displaySize": "t2.medium",
  "namespaceId": "fixme",
  "name": "api-test-template"
}
```

When creating new node templates from your user settings, you can clone an existing template and quickly update its settings rather than creating a new one from scratch. Cloning templates saves you the hassle of re-entering access keys for the cloud provider.

### HTTP Request

`POST RANCHER_SERVER_URL/v3/nodetemplate`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
useInternalIpAddress | true | ?
amazonec2Config | ? | Amazon EC2 Config - Access Credentials
accessKey | "" | AWS account access key
ami | "" | Amazon Machine Image
blockDurationMinutes | "0" | ?
endpoint | "" | ?
iamInstanceProfile | "" | IAM instance profile for the node template
insecureTransport | false | ?
instanceType | "t2.medium" | AWS instance type
keypairName | "" | Name of key pair associated with node template
monitoring | false | ?
privateAddressOnly | false | ?
region | "us-west-2" | ?
requestSpotInstance | false | ?
retries | "5" | ?
rootSize | "16" | ?
securityGroup | ["rancher-nodes"] | AWS security group
securityGroupReadonly | false | ?
sessionToken | "" | ?
spotPrice | "0.50" | ?
subnetId | subnet-a27955e9 | ?
tags | "" | ?
useEbsOptimizedInstance | false | ?
usePrivateAddress | false | ?
userdata | "" | ?
volumeType | "gp2" | ?
vpcId | "vpc-2745f35f" | ?
zone | "b" | ?
annotations | {ownerBindingsCreated: true} | false
ownerBindingsCreated | true | ?
baseType | nodeTemplate | ?
cloudCredentialId | "cattle-global-data:cc-djc44" | ?
created | "2020-01-15T19:56:16Z" | Created date
createdTS | 1579118176000 | ?
creatorId | "user-lv6bp" | ?
driver | "amazonec2" | ?
engineInstallURL | "https://releases.rancher.com/install-docker/19.03.sh" | URL to download Docker
engineRegistryMirror | null | ?
labels | {"cattle.io/creator": "norman"} | ?
principalId | "local://user-lv6bp" | ?
state | "active" | ?
transitioning | "no" | ?
transitioningMessage | "" | ?
type | "nodeTemplate" | ?
displayLocation | "us-west-2b" | ?
displaySize | "t2.medium" | ?
namespaceId | "fixme" | ?
name | "api-test-template" | ?

# Changing Settings

## Toggle Cluster Template Enforcement

```shell
curl -u "${CATTLE_ACCESS_KEY}:${CATTLE_SECRET_KEY}" \
-X PUT \
-H 'Accept: application/json' \
-H 'Content-Type: application/json' \
"${RANCHER_SERVER_URL}"
```

```shell
HTTP/1.1 PUT /v3/settings/cluster-template-enforcement
Host: ec2-35-160-22-186.us-west-2.compute.amazonaws.com
Accept: application/json
Content-Type: application/json
Content-Length: 248
{

    "created": "2020-01-15T19:49:15Z",
    "creatorId": null,
    "default": "false",
    "labels": {
        "cattle.io/creator": "norman"
    },
    "name": "cluster-template-enforcement",
    "ownerReferences": [ ],
    "source": "default",
    "uuid": "1c00322e-37d0-11ea-9ac2-0242ac110002",
    "value": "true"

}
```
You might want to require new clusters to use a template to ensure that any cluster launched by a standard user will use the Kubernetes and/or Rancher settings that are vetted by administrators.

To require new clusters to use an RKE template, administrators can turn on RKE template enforcement. The result is that all clusters provisioned by Rancher must use a template, unless the creator is an administrator.

## Configure Time Before User Membership Refresh

```shell
curl -u "${CATTLE_ACCESS_KEY}:${CATTLE_SECRET_KEY}" \
-X PUT \
-H 'Accept: application/json' \
-H 'Content-Type: application/json' \
"${RANCHER_SERVER_URL}/v3/settings/auth-user-info-max-age-seconds"

HTTP/1.1 PUT /v3/settings/auth-user-info-max-age-seconds
Host: ec2-35-160-22-186.us-west-2.compute.amazonaws.com
Accept: application/json
Content-Type: application/json
Content-Length: 249
{
"created": "2020-01-15T19:49:15Z",
"creatorId": null,
"default": "3600",
"labels": {
"cattle.io/creator": "norman"
},
"name": "auth-user-info-max-age-seconds",
"ownerReferences": [ ],
"source": "default",
"uuid": "1c12d96a-37d0-11ea-9ac2-0242ac110002",
"value": "3601"
}

```

This setting controls how old a user’s information can be before Rancher refreshes it. If a user makes an API call (either directly or by using the Rancher CLI or kubectl) and the time since the user’s last refresh is greater than this setting, then Rancher will trigger a refresh. This setting defaults to 3600 seconds, i.e. 1 hour.


# Top-level Types

Type | Description
-----|-------------
authConfigs | ?
catalogs | ?
cloudCredentials | ?
clusterAlertGroups | ?
clusterAlertRules | ?
clusterAlerts | ?
clusterCatalogs | ?
clusterLoggings | ?
clusterMonitorGraphs | ?
clusterRegistrationTokens | ?
clusterRoleTemplateBindings | ?
clusterScans | ?
clusterTemplateRevisions | ?
clusterTemplates | ?
clusters | ?
composeConfigs | ?
dynamicSchemas | ?
etcdBackups | ?
features | ?
globalRoleBindings | ?
globalRoles | ?
groupMembers | ?
groups | ?
kontainerDrivers | ?
ldapConfigs | ?
listenConfigs | ?
managementSecrets | ?
monitorMetrics | ?
multiClusterAppRevisions
multiClusterApps | ?
nodeDrivers | ?
nodePools | ?
nodeTemplates | ?
nodes | ?
notifiers | ?
podSecurityPolicyTemplateProjectBindings | ?
podSecurityPolicyTemplates | ?
preferences | ?
principals | ?
projectAlertGroups | ?
projectAlertRules | ?
projectAlerts | ?
projectCatalogs | ?
projectLoggings | ?
projectMonitorGraphs | ?
projectNetworkPolicies | ?
projectRoleTemplateBindings | ?
projects | ?
rkeAddons | ?
rkeK8sServiceOptions | ?
rkeK8sSystemImages | ?
roleTemplates | ?
root | ?
self | ?
settings | ?
subscribe | ?
templateVersions | ?
templates | ?
tokens | ?
users | ?

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

