<h2 id="auth">Authentication</h2>

<h3 id="local-auth">1.0 Logging into Rancher Locally</h3>

  <strong>1.1 API Route:</strong> 
  ``` 
  https://127.0.0.1/login
  
  ```

  <strong>1.2 Query String Params:</strong>
  ``` 
  action: login 
  
  ```

  <strong>1.3 Fully Qualified Route:</strong> 
  ``` 
  https://127.0.0.1/v3-public/localProviders/local?action=login 
  
  ```

  <strong>1.4 Payload:</strong>
  ```
  {
    username: "admin"
    password: "supersecret"
    description: "UI Session"
    responseType: "cookie"
    ttl: 57600000
    labels: {ui-session: "true"}
    ui-session: "true"
  }
  ```
    
  <strong>1.5 CRSF and Session Cookies</strong>
  
  In the header requests, you'll need add (as all one line): 
   ```
   Cookie: R_USERNAME=admin; 
   CSRF=f93a4bdb7f; 
   R_SESS=token-8blls:pvwss586wwdd46bxgcl7bghkkbbgqgc7hqgkx9rzsw65sgbsd5wzmt
   ```
  
  ![](assets/images/cookies-auth.png)

  <strong>1.6 Local Auth REST API schema:</strong>
```
{
  "actions": {
  "login": "…/v3-public/localProviders/local?action=login"
},
  "baseType": "authProvider",
  "creatorId": null,
  "id": "local",
  "links": {
  "self": "…/v3-public/localProviders/local"
},
  "type": "localProvider"
}
 ```
 
 ---
 
<h3 id="create-api-key">2.0 Create API Key</h3>

This is so you can retrieve the Bearer Token and interact as an authorized user.

  <strong>2.1 API Route:</strong> 
  ``` 
   Request URL: https://127.0.0.1/v3/token
   Request Method: POST
  
  ```
  
  <strong>2.1.1 Get the Cluster ID</strong>
  
  First, you will need to know the cluster id in order to build the correct values for the payload that is <strong>$POST</strong>'ed.
    
   A) Call on: ``` https://127.0.0.1/v3/cluster ```
   The very long response object should look like this (scroll down to 'B)' for array mapping to cluster id):
   
   ```
    {
      "type": "collection",
      "links": {
      "self": "…/v3/cluster"
      },
      "createTypes": {
      "cluster": "…/v3/clusters"
      },
      "actions": { },
      "pagination": {
      "limit": 1000,
      "total": 1
      },
      "sort": {
      "order": "asc",
      "reverse": "…/v3/cluster?order=desc",
      "links": {
      "agentImage": "…/v3/cluster?sort=agentImage",
      "apiEndpoint": "…/v3/cluster?sort=apiEndpoint",
      "appliedPodSecurityPolicyTemplateId": "…/v3/cluster?sort=appliedPodSecurityPolicyTemplateId",
      "authImage": "…/v3/cluster?sort=authImage",
      "caCert": "…/v3/cluster?sort=caCert",
      "description": "…/v3/cluster?sort=description",
      "desiredAgentImage": "…/v3/cluster?sort=desiredAgentImage",
      "desiredAuthImage": "…/v3/cluster?sort=desiredAuthImage",
      "dockerRootDir": "…/v3/cluster?sort=dockerRootDir",
      "driver": "…/v3/cluster?sort=driver",
      "state": "…/v3/cluster?sort=state",
      "transitioning": "…/v3/cluster?sort=transitioning",
      "transitioningMessage": "…/v3/cluster?sort=transitioningMessage",
      "uuid": "…/v3/cluster?sort=uuid"
      }
      },
      "filters": {
      "agentImage": null,
      "apiEndpoint": null,
      "appliedEnableNetworkPolicy": null,
      "appliedPodSecurityPolicyTemplateId": null,
      "authImage": null,
      "caCert": null,
      "created": null,
      "creatorId": null,
      "defaultClusterRoleForProjectMembers": null,
      "defaultPodSecurityPolicyTemplateId": null,
      "description": null,
      "desiredAgentImage": null,
      "desiredAuthImage": null,
      "dockerRootDir": null,
      "driver": null,
      "enableClusterAlerting": null,
      "enableClusterMonitoring": null,
      "enableNetworkPolicy": null,
      "id": null,
      "internal": null,
      "name": null,
      "removed": null,
      "state": null,
      "transitioning": null,
      "transitioningMessage": null,
      "uuid": null
      },
      "resourceType": "cluster",
      "data": [
          {
          "actions": {
          "backupEtcd": "…/v3/clusters/c-wz94t?action=backupEtcd",
          "enableMonitoring": "…/v3/clusters/c-wz94t?action=enableMonitoring",
          "exportYaml": "…/v3/clusters/c-wz94t?action=exportYaml",
          "generateKubeconfig": "…/v3/clusters/c-wz94t?action=generateKubeconfig",
          "importYaml": "…/v3/clusters/c-wz94t?action=importYaml",
          "restoreFromEtcdBackup": "…/v3/clusters/c-wz94t?action=restoreFromEtcdBackup",
          "rotateCertificates": "…/v3/clusters/c-wz94t?action=rotateCertificates"
          },
          "agentImage": "",
          "allocatable": {
          "cpu": "0",
          "memory": "0",
          "pods": "0"
          },
          "annotations": {
          "authz.management.cattle.io/creator-role-bindings": "{\"created\":[\"cluster-owner\"],\"required\":[\"cluster-owner\"]}",
          "lifecycle.cattle.io/create.cluster-agent-controller-cleanup": "true",
          "lifecycle.cattle.io/create.cluster-scoped-gc": "true",
          "lifecycle.cattle.io/create.mgmt-cluster-rbac-remove": "true"
          },
          "appliedEnableNetworkPolicy": false,
          "appliedPodSecurityPolicyTemplateId": "",
          "appliedSpec": {
          "defaultClusterRoleForProjectMembers": null,
          "defaultPodSecurityPolicyTemplateId": null,
          "description": "",
          "desiredAgentImage": "",
          "desiredAuthImage": "",
          "displayName": "",
          "dockerRootDir": "/var/lib/docker",
          "enableClusterAlerting": false,
          "enableClusterMonitoring": false,
          "enableNetworkPolicy": null,
          "internal": false,
          "localClusterAuthEndpoint": {
          "enabled": false,
          "type": "/v3/schemas/localClusterAuthEndpoint"
          },
          "type": "/v3/schemas/clusterSpec"
          },
          "authImage": "",
          "baseType": "cluster",
          "capabilities": {
          "ingressCapabilities": [
              {
              "customDefaultBackend": false,
              "ingressProvider": "Nginx",
              "type": "/v3/schemas/ingressCapabilities"
              }
              ],
              "loadBalancerCapabilities": {
              "healthCheckSupported": false,
              "type": "/v3/schemas/loadBalancerCapabilities"
              },
              "nodePoolScalingSupported": false,
              "nodePortRange": "30000-32767",
              "type": "/v3/schemas/capabilities"
              },
              "capacity": {
              "cpu": "0",
              "memory": "0",
              "pods": "0"
              },
              "conditions": [ 10 items
              {
              "status": "True",
              "type": "Pending"
              },
              {
              "lastUpdateTime": "2020-02-12T23:46:52Z",
              "message": "waiting for etcd and controlplane nodes to be registered",
              "reason": "Provisioning",
              "status": "Unknown",
              "type": "Provisioned"
              },
              {
              "lastUpdateTime": "2020-02-12T23:46:52Z",
              "message": "Waiting for API to be available",
              "status": "Unknown",
              "type": "Waiting"
              },
              {
              "lastUpdateTime": "2020-02-12T23:46:52Z",
              "status": "True",
              "type": "BackingNamespaceCreated"
              },
              {
              "lastUpdateTime": "2020-02-12T23:46:52Z",
              "status": "True",
              "type": "DefaultProjectCreated"
              },
              {
              "lastUpdateTime": "2020-02-12T23:46:52Z",
              "status": "True",
              "type": "SystemProjectCreated"
              },
              {
              "lastUpdateTime": "2020-02-12T23:46:52Z",
              "status": "True",
              "type": "InitialRolesPopulated"
              },
              {
              "lastUpdateTime": "2020-02-12T23:46:52Z",
              "status": "True",
              "type": "CreatorMadeOwner"
              },
              {
              "lastUpdateTime": "2020-02-12T23:46:52Z",
              "status": "True",
              "type": "NoDiskPressure"
              },
              {
              "lastUpdateTime": "2020-02-12T23:46:52Z",
              "status": "True",
              "type": "NoMemoryPressure"
              }
          ],
          "created": "2020-02-12T23:46:52Z",
          "createdTS": 1581551212000,
          "creatorId": "user-x57rg",
          "defaultClusterRoleForProjectMembers": null,
          "defaultPodSecurityPolicyTemplateId": null,
          "description": "",
          "desiredAgentImage": "",
          "desiredAuthImage": "",
          "dockerRootDir": "/var/lib/docker",
          "driver": "rancherKubernetesEngine",
          "enableClusterAlerting": false,
          "enableClusterMonitoring": false,
          "enableNetworkPolicy": false,
          "id": "c-wz94t",
          "internal": false,
          "labels": {
          "cattle.io/creator": "norman"
          },
          "limits": {
          "cpu": "0",
          "memory": "0",
          "pods": "0"
          },
          "links": {
          "clusterAlertGroups": "…/v3/clusters/c-wz94t/clusteralertgroups",
          "clusterAlertRules": "…/v3/clusters/c-wz94t/clusteralertrules",
          "clusterAlerts": "…/v3/clusters/c-wz94t/clusteralerts",
          "clusterCatalogs": "…/v3/clusters/c-wz94t/clustercatalogs",
          "clusterLoggings": "…/v3/clusters/c-wz94t/clusterloggings",
          "clusterMonitorGraphs": "…/v3/clusters/c-wz94t/clustermonitorgraphs",
          "clusterRegistrationTokens": "…/v3/clusters/c-wz94t/clusterregistrationtokens",
          "clusterRoleTemplateBindings": "…/v3/clusters/c-wz94t/clusterroletemplatebindings",
          "etcdBackups": "…/v3/clusters/c-wz94t/etcdbackups",
          "namespaces": "…/v3/clusters/c-wz94t/namespaces",
          "nodePools": "…/v3/clusters/c-wz94t/nodepools",
          "nodes": "…/v3/clusters/c-wz94t/nodes",
          "notifiers": "…/v3/clusters/c-wz94t/notifiers",
          "persistentVolumes": "…/v3/clusters/c-wz94t/persistentvolumes",
          "projects": "…/v3/clusters/c-wz94t/projects",
          "remove": "…/v3/clusters/c-wz94t",
          "self": "…/v3/clusters/c-wz94t",
          "shell": "wss://127.0.0.1/v3/clusters/c-wz94t?shell=true",
          "storageClasses": "…/v3/clusters/c-wz94t/storageclasses",
          "subscribe": "…/v3/clusters/c-wz94t/subscribe",
          "templates": "…/v3/clusters/c-wz94t/templates",
          "tokens": "…/v3/clusters/c-wz94t/tokens",
          "update": "…/v3/clusters/c-wz94t"
          },
          "localClusterAuthEndpoint": {
          "enabled": true,
          "type": "/v3/schemas/localClusterAuthEndpoint"
          },
          "name": "sand",
          "rancherKubernetesEngineConfig": {
          "addonJobTimeout": 30,
          "authentication": {
          "strategy": "x509|webhook",
          "type": "/v3/schemas/authnConfig"
          },
          "authorization": {
          "type": "/v3/schemas/authzConfig"
          },
          "bastionHost": {
          "sshAgentAuth": false,
          "type": "/v3/schemas/bastionHost"
          },
          "cloudProvider": {
          "type": "/v3/schemas/cloudProvider"
          },
          "ignoreDockerVersion": true,
          "ingress": {
          "provider": "nginx",
          "type": "/v3/schemas/ingressConfig"
          },
          "kubernetesVersion": "v1.13.5-rancher1-3",
          "monitoring": {
          "provider": "metrics-server",
          "type": "/v3/schemas/monitoringConfig"
          },
          "network": {
          "options": {
          "flannel_backend_type": "vxlan"
          },
          "plugin": "canal",
          "type": "/v3/schemas/networkConfig"
          },
          "restore": {
          "restore": false,
          "type": "/v3/schemas/restoreConfig"
          },
          "services": {
          "etcd": {
          "backupConfig": {
          "enabled": true,
          "intervalHours": 12,
          "retention": 6,
          "s3BackupConfig": null,
          "type": "/v3/schemas/backupConfig"
          },
          "creation": "12h",
          "extraArgs": {
          "election-timeout": "5000",
          "heartbeat-interval": "500"
          },
          "retention": "72h",
          "snapshot": false,
          "type": "/v3/schemas/etcdService"
          },
          "kubeApi": {
          "alwaysPullImages": false,
          "podSecurityPolicy": false,
          "serviceNodePortRange": "30000-32767",
          "type": "/v3/schemas/kubeAPIService"
          },
          "kubeController": {
          "type": "/v3/schemas/kubeControllerService"
          },
          "kubelet": {
          "failSwapOn": false,
          "type": "/v3/schemas/kubeletService"
          },
          "kubeproxy": {
          "type": "/v3/schemas/kubeproxyService"
          },
          "scheduler": {
          "type": "/v3/schemas/schedulerService"
          },
          "type": "/v3/schemas/rkeConfigServices"
          },
          "sshAgentAuth": false,
          "type": "/v3/schemas/rancherKubernetesEngineConfig"
          },
          "requested": {
          "cpu": "0",
          "memory": "0",
          "pods": "0"
          },
          "state": "provisioning",
          "transitioning": "yes",
          "transitioningMessage": "waiting for etcd and controlplane nodes to be registered",
          "type": "cluster",
          "uuid": "f1ce8a4c-4df1-11ea-a937-0242ac110002"
          }
      ]
}
```
  B) Map to cluster id from above payload with: ``` data["0"].id ```, which should return: ``` "id": "c-wz94t" ```.
  
  <strong>2.2 Payload:</strong>
  ```
  {
    current: false
    enabled: true
    expired: false
    isDerived: false
    ttl: 31622400000 <- How is this computed and what is this?
    type: "token"
    description: "user_token"
    clusterId: "c-wz94t" <-  data["0"].id
  }
  ```
  
  <strong>2.2 Response: </strong>
  
  Towards the bottom of the reponse object, (listed below), you will see:
  
  ```
  "token":"token-x69qs:twfj42hfbqhr2zqffrwvr5l2n5jz64rvwjbrh8tz266skv8wswxrmv"
  ```
  
  That is the bearer token you will recieve, and subsequently use with every API call for access.
  
  ```
  { 
   "authProvider":"local",
   "baseType":"token",
   "clusterId":"c-wz94t",
   "created":"2020-02-13T13:16:50Z",
   "createdTS":1581599810000,
   "creatorId":null,
   "current":false,
   "description":"user_token",
   "enabled":true,
   "expired":false,
   "expiresAt":"",
   "groupPrincipals":null,
   "id":"token-x69qs",
   "isDerived":true,
   "labels":{ 
      "authn.management.cattle.io/token-userId":"user-x57rg",
      "cattle.io/creator":"norman"
   },
   "lastUpdateTime":"",
   "links":{ 
      "remove":"https://127.0.0.1/v3/tokens/token-x69qs",
      "self":"https://127.0.0.1/v3/tokens/token-x69qs",
      "update":"https://127.0.0.1/v3/tokens/token-x69qs"
   },
   "name":"token-x69qs",
   "token":"token-x69qs:twfj42hfbqhr2zqffrwvr5l2n5jz64rvwjbrh8tz266skv8wswxrmv",
   "ttl":31622400000,
   "type":"token",
   "userId":"user-x57rg",
   "userPrincipal":"map[metadata:map[name:local://user-x57rg creationTimestamp:\u003cnil\u003e] displayName:Default Admin  
                    loginName:admin principalType:user me:true provider:local]",
   "uuid":"182bb3ea-4e63-11ea-8930-0242ac110002"
}
```















---
layout: default
---

Text can be **bold**, _italic_, or ~~strikethrough~~.

[Link to another page](./another-page.html).

There should be whitespace between paragraphs.

There should be whitespace between paragraphs. We recommend including a README, or a file with information about your project.

# Header 1

This is a normal paragraph following a header. GitHub is a code hosting platform for version control and collaboration. It lets you and others work together on projects from anywhere.

## Header 2

> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.

### Header 3

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
