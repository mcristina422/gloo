
---
title: "settings.proto"
weight: 5
---

<!-- Code generated by solo-kit. DO NOT EDIT. -->


### Package: `gloo.solo.io` 
#### Types:


- [Settings](#settings) **Top-Level Resource**
- [KubernetesCrds](#kubernetescrds)
- [KubernetesSecrets](#kubernetessecrets)
- [VaultSecrets](#vaultsecrets)
- [ConsulKv](#consulkv)
- [KubernetesConfigmaps](#kubernetesconfigmaps)
- [Directory](#directory)
- [KnativeOptions](#knativeoptions)
- [DiscoveryOptions](#discoveryoptions)
- [FdsMode](#fdsmode)
- [ConsulConfiguration](#consulconfiguration)
- [ServiceDiscoveryOptions](#servicediscoveryoptions)
- [ConsulUpstreamDiscoveryConfiguration](#consulupstreamdiscoveryconfiguration)
- [KubernetesConfiguration](#kubernetesconfiguration)
- [RateLimits](#ratelimits)
- [ObservabilityOptions](#observabilityoptions)
- [GrafanaIntegration](#grafanaintegration)
- [UpstreamOptions](#upstreamoptions)
- [GlooOptions](#gloooptions)
- [AWSOptions](#awsoptions)
- [InvalidConfigPolicy](#invalidconfigpolicy)
- [VirtualServiceOptions](#virtualserviceoptions)
- [GatewayOptions](#gatewayoptions)
- [ValidationOptions](#validationoptions)
  



##### Source File: [github.com/solo-io/gloo/projects/gloo/api/v1/settings.proto](https://github.com/solo-io/gloo/blob/master/projects/gloo/api/v1/settings.proto)





---
### Settings

 
Represents global settings for all the Gloo components.

```yaml
"discoveryNamespace": string
"watchNamespaces": []string
"kubernetesConfigSource": .gloo.solo.io.Settings.KubernetesCrds
"directoryConfigSource": .gloo.solo.io.Settings.Directory
"consulKvSource": .gloo.solo.io.Settings.ConsulKv
"kubernetesSecretSource": .gloo.solo.io.Settings.KubernetesSecrets
"vaultSecretSource": .gloo.solo.io.Settings.VaultSecrets
"directorySecretSource": .gloo.solo.io.Settings.Directory
"kubernetesArtifactSource": .gloo.solo.io.Settings.KubernetesConfigmaps
"directoryArtifactSource": .gloo.solo.io.Settings.Directory
"consulKvArtifactSource": .gloo.solo.io.Settings.ConsulKv
"refreshRate": .google.protobuf.Duration
"devMode": bool
"linkerd": bool
"knative": .gloo.solo.io.Settings.KnativeOptions
"discovery": .gloo.solo.io.Settings.DiscoveryOptions
"gloo": .gloo.solo.io.GlooOptions
"gateway": .gloo.solo.io.GatewayOptions
"consul": .gloo.solo.io.Settings.ConsulConfiguration
"consulDiscovery": .gloo.solo.io.Settings.ConsulUpstreamDiscoveryConfiguration
"kubernetes": .gloo.solo.io.Settings.KubernetesConfiguration
"extensions": .gloo.solo.io.Extensions
"ratelimit": .ratelimit.options.gloo.solo.io.ServiceSettings
"ratelimitServer": .ratelimit.options.gloo.solo.io.Settings
"rbac": .rbac.options.gloo.solo.io.Settings
"extauth": .enterprise.gloo.solo.io.Settings
"namedExtauth": map<string, .enterprise.gloo.solo.io.Settings>
"metadata": .core.solo.io.Metadata
"status": .core.solo.io.Status
"observabilityOptions": .gloo.solo.io.Settings.ObservabilityOptions
"upstreamOptions": .gloo.solo.io.UpstreamOptions

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `discoveryNamespace` | `string` | This is the namespace to which Gloo controllers will write their own resources, e.g. discovered Upstreams or default Gateways. If empty, this will default to "gloo-system". |
| `watchNamespaces` | `[]string` | Use this setting to restrict the namespaces that Gloo controllers take into consideration when watching for resources.In a usual production scenario, RBAC policies will limit the namespaces that Gloo has access to. If `watch_namespaces` contains namespaces outside of this whitelist, Gloo will fail to start. If not set, this defaults to all available namespaces. Please note that, the `discovery_namespace` will always be included in this list. |
| `kubernetesConfigSource` | [.gloo.solo.io.Settings.KubernetesCrds](../settings.proto.sk/#kubernetescrds) |  Only one of `kubernetesConfigSource`, or `consulKvSource` can be set. |
| `directoryConfigSource` | [.gloo.solo.io.Settings.Directory](../settings.proto.sk/#directory) |  Only one of `directoryConfigSource`, or `consulKvSource` can be set. |
| `consulKvSource` | [.gloo.solo.io.Settings.ConsulKv](../settings.proto.sk/#consulkv) |  Only one of `consulKvSource`, or `directoryConfigSource` can be set. |
| `kubernetesSecretSource` | [.gloo.solo.io.Settings.KubernetesSecrets](../settings.proto.sk/#kubernetessecrets) |  Only one of `kubernetesSecretSource`, or `directorySecretSource` can be set. |
| `vaultSecretSource` | [.gloo.solo.io.Settings.VaultSecrets](../settings.proto.sk/#vaultsecrets) |  Only one of `vaultSecretSource`, or `directorySecretSource` can be set. |
| `directorySecretSource` | [.gloo.solo.io.Settings.Directory](../settings.proto.sk/#directory) |  Only one of `directorySecretSource`, or `vaultSecretSource` can be set. |
| `kubernetesArtifactSource` | [.gloo.solo.io.Settings.KubernetesConfigmaps](../settings.proto.sk/#kubernetesconfigmaps) |  Only one of `kubernetesArtifactSource`, or `consulKvArtifactSource` can be set. |
| `directoryArtifactSource` | [.gloo.solo.io.Settings.Directory](../settings.proto.sk/#directory) |  Only one of `directoryArtifactSource`, or `consulKvArtifactSource` can be set. |
| `consulKvArtifactSource` | [.gloo.solo.io.Settings.ConsulKv](../settings.proto.sk/#consulkv) |  Only one of `consulKvArtifactSource`, or `directoryArtifactSource` can be set. |
| `refreshRate` | [.google.protobuf.Duration](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/duration) | How frequently to resync watches, etc. |
| `devMode` | `bool` | Enable serving debug data on port 9090. |
| `linkerd` | `bool` | Enable automatic linkerd upstream header addition for easier routing to linkerd services. |
| `knative` | [.gloo.solo.io.Settings.KnativeOptions](../settings.proto.sk/#knativeoptions) | Configuration options for the Clusteringress Controller (for Knative). |
| `discovery` | [.gloo.solo.io.Settings.DiscoveryOptions](../settings.proto.sk/#discoveryoptions) | Options for configuring Gloo's Discovery service. |
| `gloo` | [.gloo.solo.io.GlooOptions](../settings.proto.sk/#gloooptions) | Options for configuring `gloo`, the core Gloo controller, which serves dynamic configuration to Envoy. |
| `gateway` | [.gloo.solo.io.GatewayOptions](../settings.proto.sk/#gatewayoptions) | Options for configuring `gateway`, the Gateway Gloo controller, which enables the VirtualService/Gateway API in Gloo. |
| `consul` | [.gloo.solo.io.Settings.ConsulConfiguration](../settings.proto.sk/#consulconfiguration) | Options to configure Gloo's integration with [HashiCorp Consul](https://www.consul.io/). |
| `consulDiscovery` | [.gloo.solo.io.Settings.ConsulUpstreamDiscoveryConfiguration](../settings.proto.sk/#consulupstreamdiscoveryconfiguration) |  |
| `kubernetes` | [.gloo.solo.io.Settings.KubernetesConfiguration](../settings.proto.sk/#kubernetesconfiguration) | Options to configure Gloo's integration with [Kubernetes](https://www.kubernetes.io/). |
| `extensions` | [.gloo.solo.io.Extensions](../extensions.proto.sk/#extensions) | Extensions will be passed along from Listeners, Gateways, VirtualServices, Routes, and Route tables to the underlying Proxy, making them useful for controllers, validation tools, etc. which interact with kubernetes yaml. Some sample use cases: * controllers, deployment pipelines, helm charts, etc. which wish to use extensions as a kind of opaque metadata. * In the future, Gloo may support gRPC-based plugins which communicate with the Gloo translator out-of-process. Opaque Extensions enables development of out-of-process plugins without requiring recompiling & redeploying Gloo's API. |
| `ratelimit` | [.ratelimit.options.gloo.solo.io.ServiceSettings](../enterprise/options/ratelimit/ratelimit.proto.sk/#servicesettings) | Enterprise-only: Partial config for GlooE's rate-limiting service, based on Envoy's rate-limit service; supports Envoy's rate-limit service API. (reference here: https://github.com/lyft/ratelimit#configuration) Configure rate-limit *descriptors* here, which define the limits for requests based on their descriptors. Configure rate-limits (composed of *actions*, which define how request characteristics get translated into descriptors) on the VirtualHost or its routes. |
| `ratelimitServer` | [.ratelimit.options.gloo.solo.io.Settings](../enterprise/options/ratelimit/ratelimit.proto.sk/#settings) | Enterprise-only: Settings for the rate limiting server itself. |
| `rbac` | [.rbac.options.gloo.solo.io.Settings](../enterprise/options/rbac/rbac.proto.sk/#settings) | Enterprise-only: Settings for RBAC across all Gloo resources (VirtualServices, Routes, etc.). |
| `extauth` | [.enterprise.gloo.solo.io.Settings](../enterprise/options/extauth/v1/extauth.proto.sk/#settings) | Enterprise-only: External auth related settings. |
| `namedExtauth` | `map<string, .enterprise.gloo.solo.io.Settings>` | Enterprise-only: External auth related settings for additional auth servers This should only be used in the case where separate servers are needed to authorize separate routes. With multiple auth servers configured in Settings, multiple filters will be configured on the filter chain, but only 1 will be executed on a route. The name of the auth server (ie the key in the map) will be used to apply the configuration on the route. If an auth server name is not supplied on a route, the default auth server will be applied. |
| `metadata` | [.core.solo.io.Metadata](../../../../../../solo-kit/api/v1/metadata.proto.sk/#metadata) | Metadata contains the object metadata for this resource. |
| `status` | [.core.solo.io.Status](../../../../../../solo-kit/api/v1/status.proto.sk/#status) | Status indicates the validation status of this resource. Status is read-only by clients, and set by gloo during validation. |
| `observabilityOptions` | [.gloo.solo.io.Settings.ObservabilityOptions](../settings.proto.sk/#observabilityoptions) | Provides settings related to the observability deployment (enterprise only). |
| `upstreamOptions` | [.gloo.solo.io.UpstreamOptions](../settings.proto.sk/#upstreamoptions) | Default configuration to use for upstreams, when not provided by specific upstream When these properties are defined on an upstream, this configuration will be ignored. |




---
### KubernetesCrds

 
Use Kubernetes CRDs as storage.

```yaml

```

| Field | Type | Description |
| ----- | ---- | ----------- | 




---
### KubernetesSecrets

 
Use Kubernetes as storage for secret data.

```yaml

```

| Field | Type | Description |
| ----- | ---- | ----------- | 




---
### VaultSecrets

 
Use [HashiCorp Vault](https://www.vaultproject.io/) as storage for secret data.

```yaml
"token": string
"address": string
"caCert": string
"caPath": string
"clientCert": string
"clientKey": string
"tlsServerName": string
"insecure": .google.protobuf.BoolValue
"rootKey": string

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `token` | `string` | the Token used to authenticate to Vault. |
| `address` | `string` | address is the address of the Vault server. This should be a complete URL such as http://solo.io. |
| `caCert` | `string` | caCert is the path to a PEM-encoded CA cert file to use to verify the Vault server SSL certificate. |
| `caPath` | `string` | caPath is the path to a directory of PEM-encoded CA cert files to verify the Vault server SSL certificate. |
| `clientCert` | `string` | clientCert is the path to the certificate for Vault communication. |
| `clientKey` | `string` | clientKey is the path to the private key for Vault communication. |
| `tlsServerName` | `string` | tlsServerName, if set, is used to set the SNI host when connecting via TLS. |
| `insecure` | [.google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value) | Insecure enables or disables SSL verification. |
| `rootKey` | `string` | all keys stored in Vault will begin with this Vault this can be used to run multiple instances of Gloo against the same Consul cluster defaults to `gloo`. |




---
### ConsulKv

 
Use [HashiCorp Consul Key-Value](https://www.consul.io/api/kv.html/) as storage for config data.
Configuration options for connecting to Consul can be configured in the Settings' root
`consul` field

```yaml
"rootKey": string

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `rootKey` | `string` | all keys stored in Consul will begin with this prefix this can be used to run multiple instances of Gloo against the same Consul cluster defaults to `gloo`. |




---
### KubernetesConfigmaps

 
Use Kubernetes ConfigMaps as storage.

```yaml

```

| Field | Type | Description |
| ----- | ---- | ----------- | 




---
### Directory

 
As an alternative to Kubernetes CRDs, Gloo is able to store resources in a local file system.
This option determines the root of the directory tree used to this end.

```yaml
"directory": string

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `directory` | `string` |  |




---
### KnativeOptions



```yaml
"clusterIngressProxyAddress": string
"knativeExternalProxyAddress": string
"knativeInternalProxyAddress": string

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `clusterIngressProxyAddress` | `string` | Address of the clusteringress proxy. If empty, it will default to clusteringress-proxy.$POD_NAMESPACE.svc.cluster.local. Use if running Knative Version 0.7.X or less. |
| `knativeExternalProxyAddress` | `string` | Address of the externally-facing knative proxy. If empty, it will default to knative-external-proxy.$POD_NAMESPACE.svc.cluster.local. Use if running Knative Version 0.8.X or higher. |
| `knativeInternalProxyAddress` | `string` | Address of the internally-facing knative proxy. If empty, it will default to knative-internal-proxy.$POD_NAMESPACE.svc.cluster.local. Use if running Knative Version 0.8.X or higher. |




---
### DiscoveryOptions



```yaml
"fdsMode": .gloo.solo.io.Settings.DiscoveryOptions.FdsMode

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `fdsMode` | [.gloo.solo.io.Settings.DiscoveryOptions.FdsMode](../settings.proto.sk/#fdsmode) |  |




---
### FdsMode

 
Possible modes for running the function discovery service (FDS). FDS polls services in-cluster for Swagger
and gRPC endpoints. This behavior can be controlled with the use of annotations.
FdsMode specifies what policy FDS will use when determining which services to poll.

| Name | Description |
| ----- | ----------- | 
| `BLACKLIST` | In BLACKLIST mode (default), FDS will poll all services in cluster except those services labeled with `discovery.solo.io/function_discovery=disabled`. This label can also be used on namespaces to apply to all services within a namespace **which are not explicitly whitelisted**. Note that `kube-system` and `kube-public` namespaces must be explicitly whitelisted even in blacklist mode. |
| `WHITELIST` | In WHITELIST mode, FDS will poll only services in cluster labeled with `discovery.solo.io/function_discovery=enabled`. This label can also be used on namespaces to apply to all services **which are not explicitly blacklisted** within a namespace. |
| `DISABLED` | In DISABLED mode, FDS will not run. |




---
### ConsulConfiguration

 
Provides overrides for the default configuration parameters used to connect to Consul.

Note: It is also possible to configure the Consul client Gloo uses via the environment variables
described [here](https://www.consul.io/docs/commands/index.html#environment-variables). These
need to be set on the Gloo container.

```yaml
"address": string
"datacenter": string
"username": string
"password": string
"token": string
"caFile": string
"caPath": string
"certFile": string
"keyFile": string
"insecureSkipVerify": .google.protobuf.BoolValue
"waitTime": .google.protobuf.Duration
"serviceDiscovery": .gloo.solo.io.Settings.ConsulConfiguration.ServiceDiscoveryOptions
"httpAddress": string
"dnsAddress": string
"dnsPollingInterval": .google.protobuf.Duration

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `address` | `string` | Deprecated: prefer http_address. The address of the Consul HTTP server. Used by service discovery and key-value storage (if-enabled). Defaults to the value of the standard CONSUL_HTTP_ADDR env if set, otherwise to 127.0.0.1:8500. |
| `datacenter` | `string` | Datacenter to use. If not provided, the default agent datacenter is used. |
| `username` | `string` | Username to use for HTTP Basic Authentication. |
| `password` | `string` | Password to use for HTTP Basic Authentication. |
| `token` | `string` | Token is used to provide a per-request ACL token which overrides the agent's default token. |
| `caFile` | `string` | caFile is the optional path to the CA certificate used for Consul communication, defaults to the system bundle if not specified. |
| `caPath` | `string` | caPath is the optional path to a directory of CA certificates to use for Consul communication, defaults to the system bundle if not specified. |
| `certFile` | `string` | CertFile is the optional path to the certificate for Consul communication. If this is set then you need to also set KeyFile. |
| `keyFile` | `string` | KeyFile is the optional path to the private key for Consul communication. If this is set then you need to also set CertFile. |
| `insecureSkipVerify` | [.google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value) | InsecureSkipVerify if set to true will disable TLS host verification. |
| `waitTime` | [.google.protobuf.Duration](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/duration) | WaitTime limits how long a watches for Consul resources will block. If not provided, the agent default values will be used. |
| `serviceDiscovery` | [.gloo.solo.io.Settings.ConsulConfiguration.ServiceDiscoveryOptions](../settings.proto.sk/#servicediscoveryoptions) | Enable Service Discovery via Consul with this field set to empty struct `{}` to enable with defaults. |
| `httpAddress` | `string` | The address of the Consul HTTP server. Used by service discovery and key-value storage (if-enabled). Defaults to the value of the standard CONSUL_HTTP_ADDR env if set, otherwise to 127.0.0.1:8500. |
| `dnsAddress` | `string` | The address of the DNS server used to resolve hostnames in the Consul service address. Used by service discovery (required when Consul service instances are stored as DNS names). Defaults to 127.0.0.1:8600. (the default Consul DNS server). |
| `dnsPollingInterval` | [.google.protobuf.Duration](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/duration) | The polling interval for the DNS server. If there is a Consul service address with a hostname instead of an IP, Gloo will resolve the hostname with the configured frequency to update endpoints with any changes to DNS resolution. Defaults to 5s. |




---
### ServiceDiscoveryOptions

 
service discovery options for Consul

```yaml
"dataCenters": []string

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `dataCenters` | `[]string` | Use this parameter to restrict the data centers that will be considered when discovering and routing to services. If not provided, Gloo will use all available data centers. |




---
### ConsulUpstreamDiscoveryConfiguration

 
Settings related to gloo's behavior when discovering consul services and creating
upstreams to connect to those services and their instances.

```yaml
"useTlsTagging": bool
"tlsTagName": string
"rootCa": .core.solo.io.ResourceRef
"splitTlsServices": bool

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `useTlsTagging` | `bool` | If true, then gloo will add TLS to upstreams created for any consul service that has the tag specified by tlsTagName. If splitTlsServices is true, then this tag is also used to identify serviceInstances that should be tied to the TLS upstream. Requires rootCa to be set if true. |
| `tlsTagName` | `string` | The tag that gloo should use to make TLS upstreams from consul services, and to partition consul serviceInstances between TLS/non-TLS upstreams. Defaults to 'glooUseTls'. |
| `rootCa` | [.core.solo.io.ResourceRef](../../../../../../solo-kit/api/v1/ref.proto.sk/#resourceref) | The reference for the root CA resource to be used by discovered consul TLS upstreams. |
| `splitTlsServices` | `bool` | If true, then create two upstreams when the tlsTagName is found on a consul service, one with tls and one without. This requires a consul service's serviceInstances be individually tagged; servicesInstances with the tlsTagName tag are directed to the TLS upstream, while those without the tlsTagName tag are sorted into the non-TLS upstream. |




---
### KubernetesConfiguration

 
Provides overrides for the default configuration parameters used to interact with Kubernetes.

```yaml
"rateLimits": .gloo.solo.io.Settings.KubernetesConfiguration.RateLimits

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `rateLimits` | [.gloo.solo.io.Settings.KubernetesConfiguration.RateLimits](../settings.proto.sk/#ratelimits) | Rate limits for the kubernetes clients. |




---
### RateLimits



```yaml
"qPS": float
"burst": int

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `qPS` | `float` | The maximum queries-per-second Gloo can make to the Kubernetes API Server. |
| `burst` | `int` | Maximum burst for throttle. When a steady state of QPS requests per second, this is an additional number of allowed, to allow for short bursts. |




---
### ObservabilityOptions



```yaml
"grafanaIntegration": .gloo.solo.io.Settings.ObservabilityOptions.GrafanaIntegration

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `grafanaIntegration` | [.gloo.solo.io.Settings.ObservabilityOptions.GrafanaIntegration](../settings.proto.sk/#grafanaintegration) | Options to configure Gloo's integration with [Kubernetes](https://www.kubernetes.io/). |




---
### GrafanaIntegration

 
Provides settings related to the observability pod's interactions with grafana

```yaml
"defaultDashboardFolderId": .google.protobuf.UInt32Value

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `defaultDashboardFolderId` | [.google.protobuf.UInt32Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/u-int-32-value) | (UInt32Value) Grafana allows dashboards to be added to specific folders by specifying that folder's ID If unset, automatic upstream dashboards are generated in the general folder (folderId: 0). If set, the observability deployment will try to create/move all upstreams without their own folderId to the folder specified here, after verifying that a folder with such an ID exists. Be aware that grafana requires a folders ID, which should not be confused with the similarly-named and more easily accessible folder UID value. If individual upstream dashboards need to be placed specific granafa folders, they can be given their own folder IDs by annotating the upstreams. The annotation key must be 'observability.solo.io/dashboard_folder_id' and the value must be the folder ID. Folder IDs can be retrieved from grafana with a pair of terminal commands: 1. Port forward the grafana deployment to surface its API: kubectl -n gloo-system port-forward deployment/glooe-grafana 3000 2. Request all folder data (after admin:admin is replaced with the correct credentials): curl http://admin:admin@localhost:3000/api/folders. |




---
### UpstreamOptions

 
Default configuration to use for upstreams, when not provided by a specific upstream
When these properties are defined on a specific upstream, this configuration will be ignored

```yaml
"sslParameters": .gloo.solo.io.SslParameters

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `sslParameters` | [.gloo.solo.io.SslParameters](../ssl.proto.sk/#sslparameters) | Default ssl parameter configuration to use for upstreams. |




---
### GlooOptions

 
Settings specific to the gloo (Envoy xDS server) controller

```yaml
"xdsBindAddr": string
"validationBindAddr": string
"circuitBreakers": .gloo.solo.io.CircuitBreakerConfig
"endpointsWarmingTimeout": .google.protobuf.Duration
"awsOptions": .gloo.solo.io.GlooOptions.AWSOptions
"invalidConfigPolicy": .gloo.solo.io.GlooOptions.InvalidConfigPolicy
"disableKubernetesDestinations": bool
"disableGrpcWeb": .google.protobuf.BoolValue
"disableProxyGarbageCollection": .google.protobuf.BoolValue
"regexMaxProgramSize": .google.protobuf.UInt32Value
"restXdsBindAddr": string
"enableRestEds": .google.protobuf.BoolValue
"failoverUpstreamDnsPollingInterval": .google.protobuf.Duration

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `xdsBindAddr` | `string` | Where the `gloo` xDS server should bind. Defaults to `0.0.0.0:9977`. |
| `validationBindAddr` | `string` | Where the `gloo` validation server should bind. Defaults to `0.0.0.0:9988`. |
| `circuitBreakers` | [.gloo.solo.io.CircuitBreakerConfig](../circuit_breaker.proto.sk/#circuitbreakerconfig) | Default circuit breaker configuration to use for upstream requests, when not provided by specific upstream. |
| `endpointsWarmingTimeout` | [.google.protobuf.Duration](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/duration) | Timeout to get initial snapshot of resources. If set to zero, Gloo will not wait for initial snapshot - if nonzero and gloo could not fetch it's initial snapshot before the timeout reached, gloo will panic. If unset, Gloo defaults to 5 minutes. |
| `awsOptions` | [.gloo.solo.io.GlooOptions.AWSOptions](../settings.proto.sk/#awsoptions) |  |
| `invalidConfigPolicy` | [.gloo.solo.io.GlooOptions.InvalidConfigPolicy](../settings.proto.sk/#invalidconfigpolicy) | set these options to fine-tune the way Gloo handles invalid user configuration. |
| `disableKubernetesDestinations` | `bool` | Gloo allows you to directly reference a Kubernetes service as a routing destination. To enable this feature, Gloo scans the cluster for Kubernetes services and creates a special type of in-memory Upstream to represent them. If the cluster contains a lot of services and you do not restrict the namespaces Gloo is watching, this can result in significant overhead. If you do not plan on using this feature, you can use this flag to turn it off. |
| `disableGrpcWeb` | [.google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value) | Default policy for grpc-web. set to true if you do not wish grpc-web to be automatically enabled. set to false if you wish grpc-web enabled unless disabled on the listener level. If not specified, defaults to `false`. |
| `disableProxyGarbageCollection` | [.google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value) | Set this option to determine the state of the envoy configuration when a virtual service is deleted, resulting in a proxy with no configured routes. set to true if you wish to keep envoy serving the routes from the latest valid configuration. set to false if you wish to reset the envoy configuration to a clean slate with no routes. If not specified, defaults to `false`. |
| `regexMaxProgramSize` | [.google.protobuf.UInt32Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/u-int-32-value) | Set this option to specify the default max program size for regexes. If not specified, defaults to 100. |
| `restXdsBindAddr` | `string` | Where the `gloo` REST xDS server should bind. Defaults to `0.0.0.0:9976`. |
| `enableRestEds` | [.google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value) | Whether or not to use rest xds for all EDS by default. Rest XDS, as opposed to grpc, uses http polling rather than streaming. |
| `failoverUpstreamDnsPollingInterval` | [.google.protobuf.Duration](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/duration) | The polling interval for the DNS server if upstream failover is configured. If there is a failover upstream address with a hostname instead of an IP, Gloo will resolve the hostname with the configured frequency to update endpoints with any changes to DNS resolution. Defaults to 10s. |




---
### AWSOptions



```yaml
"enableCredentialsDiscovey": bool
"serviceAccountCredentials": .envoy.config.filter.http.aws_lambda.v2.AWSLambdaConfig.ServiceAccountCredentials

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `enableCredentialsDiscovey` | `bool` | Enable credential discovery via IAM; when this is set, there's no need provide a secret on the upstream when running on AWS environment. Note: This should **ONLY** be enabled when running in an AWS environment, as the AWS code blocks the envoy main thread. This should be negligible when running inside AWS. Only one of `enableCredentialsDiscovey` or `serviceAccountCredentials` can be set. |
| `serviceAccountCredentials` | [.envoy.config.filter.http.aws_lambda.v2.AWSLambdaConfig.ServiceAccountCredentials](../../external/envoy/extensions/aws/filter.proto.sk/#serviceaccountcredentials) | Use projected service account token, and role arn to create temporary credentials with which to authenticate lambda requests. This functionality is meant to work along side EKS service account to IAM binding functionality as outlined here: https://docs.aws.amazon.com/eks/latest/userguide/iam-roles-for-service-accounts.html If the following environment values are not present in the gateway-proxy, this option cannot be used. 1. AWS_WEB_IDENTITY_TOKEN_FILE 2. AWS_ROLE_ARN The role which will be assumed by the credentials will be the one specified by AWS_ROLE_ARN, however, this can also be overwritten in the AWS Upstream spec via the role_arn field If they are not specified envoy will NACK the config update, which will show up in the logs when running OS Gloo. When running Gloo enterprise it will be reflected in the prometheus stat: "glooe.solo.io/xds/nack" In order to specify the aws sts endpoint, both the cluster and uri must be set. This is due to an envoy limitation which cannot infer the host or path from the cluster, and therefore must be explicitly specified via the uri. Only one of `serviceAccountCredentials` or `enableCredentialsDiscovey` can be set. |




---
### InvalidConfigPolicy

 
Policy for how Gloo should handle invalid config

```yaml
"replaceInvalidRoutes": bool
"invalidRouteResponseCode": int
"invalidRouteResponseBody": string

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `replaceInvalidRoutes` | `bool` | if set to `true`, Gloo removes any routes from the provided configuration which point to a missing destination. Routes that are removed in this way will instead return a configurable direct response to clients. When routes are replaced, Gloo will configure Envoy with a special listener which serves direct responses. Note: enabling this option allows Gloo to accept partially valid proxy configurations. |
| `invalidRouteResponseCode` | `int` | replaced routes reply to clients with this response code. default is 404. |
| `invalidRouteResponseBody` | `string` | replaced routes reply to clients with this response body. default is 'Gloo Gateway has invalid configuration. Administrators should run `glooctl check` to find and fix config errors.'. |




---
### VirtualServiceOptions

 
Default configuration to use for VirtualServices, when not provided by a specific virtual service
When these properties are defined on a specific VirtualService, this configuration will be ignored

```yaml
"oneWayTls": .google.protobuf.BoolValue

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `oneWayTls` | [.google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value) | Default one_way_tls value to use for all virtual services where one_way_tls config has not been specified. If the SSL config has the ca.crt (root CA) provided, Gloo uses it to perform mTLS by default. Set oneWayTls to true to disable mTLS in favor of server-only TLS (one-way TLS), even if Gloo has the root CA. |




---
### GatewayOptions

 
Settings specific to the Gateway controller

```yaml
"validationServerAddr": string
"validation": .gloo.solo.io.GatewayOptions.ValidationOptions
"readGatewaysFromAllNamespaces": bool
"alwaysSortRouteTableRoutes": bool
"compressedProxySpec": bool
"virtualServiceOptions": .gloo.solo.io.VirtualServiceOptions

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `validationServerAddr` | `string` | Address of the `gloo` config validation server. Defaults to `gloo:9988`. |
| `validation` | [.gloo.solo.io.GatewayOptions.ValidationOptions](../settings.proto.sk/#validationoptions) | If provided, the Gateway will perform [Dynamic Admission Control](https://kubernetes.io/docs/reference/access-authn-authz/extensible-admission-controllers/) of Gateways, Virtual Services, and Route Tables when running in Kubernetes. |
| `readGatewaysFromAllNamespaces` | `bool` | When true, the Gateway controller will consume Gateway custom resources from all watch namespaces, rather than just the Gateway CRDs in its own namespace. |
| `alwaysSortRouteTableRoutes` | `bool` | Deprecated. This setting is ignored. Maintained for backwards compatibility with settings exposed on 1.2.x branch of Gloo. |
| `compressedProxySpec` | `bool` | If set, compresses proxy space. This can help make the Proxy CRD smaller to fit in etcd. This is an advanced option. Use with care. |
| `virtualServiceOptions` | [.gloo.solo.io.VirtualServiceOptions](../settings.proto.sk/#virtualserviceoptions) | Default configuration to use for VirtualServices, when not provided by a specific virtual service When these properties are defined on a specific VirtualService, this configuration will be ignored. |




---
### ValidationOptions

 
options for configuring admission control / validation

```yaml
"proxyValidationServerAddr": string
"validationWebhookTlsCert": string
"validationWebhookTlsKey": string
"ignoreGlooValidationFailure": bool
"alwaysAccept": .google.protobuf.BoolValue
"allowWarnings": .google.protobuf.BoolValue
"warnRouteShortCircuiting": .google.protobuf.BoolValue
"disableTransformationValidation": .google.protobuf.BoolValue
"validationServerGrpcMaxSizeBytes": .google.protobuf.Int32Value

```

| Field | Type | Description |
| ----- | ---- | ----------- | 
| `proxyValidationServerAddr` | `string` | Address of the `gloo` proxy validation grpc server. Defaults to `gloo:9988`. This field is required in order to enable fine-grained admission control. |
| `validationWebhookTlsCert` | `string` | Path to TLS Certificate for Kubernetes Validating webhook. Defaults to `/etc/gateway/validation-certs/tls.crt`. |
| `validationWebhookTlsKey` | `string` | Path to TLS Private Key for Kubernetes Validating webhook. Defaults to `/etc/gateway/validation-certs/tls.key`. |
| `ignoreGlooValidationFailure` | `bool` | When Gateway cannot communicate with Gloo (e.g. Gloo is offline) resources will be rejected by default. Enable the `ignoreGlooValidationFailure` to prevent the Validation server from rejecting resources due to network errors. |
| `alwaysAccept` | [.google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value) | Always accept resources even if validation produced an error. Validation will still log the error and increment the validation.gateway.solo.io/resources_rejected stat. Currently defaults to true - must be set to `false` to prevent writing invalid resources to storage. |
| `allowWarnings` | [.google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value) | Accept resources if validation produced a warning (defaults to true). By setting to false, this means that validation will start rejecting resources that would result in warnings, rather than just those that would result in errors. |
| `warnRouteShortCircuiting` | [.google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value) | Write a warning to route resources if validation produced a route ordering warning (defaults to false). By setting to true, this means that Gloo will start assigning warnings to resources that would result in route short-circuiting within a virtual host, for example: - prefix routes that make later routes unreachable - regex routes that make later routes unreachable - duplicate matchers. |
| `disableTransformationValidation` | [.google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value) | By default gloo will attempt to validate transformations by calling out to a local envoy binary in `validate` mode. Calling this local envoy binary can become slow when done many times during a single validation. Setting this to true will stop gloo from calling out to envoy to validate the transformations, which may speed up the validation time considerably, but may also cause the transformation config to fail after being sent to envoy. When disabling this, ensure that your transformations are valid prior to applying them. |
| `validationServerGrpcMaxSizeBytes` | [.google.protobuf.Int32Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int-32-value) | By default, gRPC validation messages between gateway and gloo pods have a max message size of 4 MB. Setting this value sets the gRPC max message size in bytes for the gloo validation server. This should only be changed if necessary. If not included, the gRPC max message size will be the default of 4 MB. |





<!-- Start of HubSpot Embed Code -->
<script type="text/javascript" id="hs-script-loader" async defer src="//js.hs-scripts.com/5130874.js"></script>
<!-- End of HubSpot Embed Code -->
