# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## 0.7.0

### Changed
- Don't log errors on normal connection closing [#206](https://github.com/ngrok/kubernetes-ingress-controller/pull/206).
- Updated `golang.org/x/net` to `0.9.0` [#215](https://github.com/ngrok/kubernetes-ingress-controller/pull/215).

### Fixed
- Add support for named service ports [#222](https://github.com/ngrok/kubernetes-ingress-controller/pull/222).


## 0.6.0
### Changed
- Added Ingress controller version to user-agent [#198](https://github.com/ngrok/kubernetes-ingress-controller/pull/198).
- Don't default to development mode for logging [#199](https://github.com/ngrok/kubernetes-ingress-controller/pull/199).

### Fixed
- Leaking TCP connections for every tunnel dial [#203](https://github.com/ngrok/kubernetes-ingress-controller/pull/203).


## 0.5.0
### Changed
- Bumped go version to 1.20 [#167](https://github.com/ngrok/kubernetes-ingress-controller/pull/167)
- Refactored Route Module Updates to be lazy [#168](https://github.com/ngrok/kubernetes-ingress-controller/pull/168)
- Annotations for configuration have been removed in favor of grouping module configurations together in `NgrokModuleSet` custom resources [#170](https://github.com/ngrok/kubernetes-ingress-controller/pull/170)

### Added
- Ran go mod tidy and added check to make sure its tidy before merge [#166](https://github.com/ngrok/kubernetes-ingress-controller/pull/166)
- Added `NgrokModuleSet` CRD [#170](https://github.com/ngrok/kubernetes-ingress-controller/pull/170)
- Added support for Circuit Breaker route module [#171](https://github.com/ngrok/kubernetes-ingress-controller/pull/171)
- Added support for OIDC route module [#173](https://github.com/ngrok/kubernetes-ingress-controller/pull/173)
- Added support for SAML route module [#186](https://github.com/ngrok/kubernetes-ingress-controller/pull/186)
- Added support for OAuth route module [#192](https://github.com/ngrok/kubernetes-ingress-controller/pull/192)
## 0.4.0
### Changed
- When no region override is passed to helm, the controller now does not default to the US and instead uses the closes geographic edge servers [#160](https://github.com/ngrok/kubernetes-ingress-controller/pull/160)
- Ingress Class has Default set to false [#109](https://github.com/ngrok/kubernetes-ingress-controller/pull/109)

### Added
- Allow controller name to be configured to support multiple ngrok ingress classes [#159](https://github.com/ngrok/kubernetes-ingress-controller/pull/159)
- Allow the controller to be configured to only watch a single namespace [#157](https://github.com/ngrok/kubernetes-ingress-controller/pull/157)
- Pass key/value pairs to helm that get added as json string metadata in ngrok api resources [#156](https://github.com/ngrok/kubernetes-ingress-controller/pull/156)
- merge all ingress objects into a single store to derive Edges. [#129](https://github.com/ngrok/kubernetes-ingress-controller/pull/129), [#10](https://github.com/ngrok/kubernetes-ingress-controller/pull/10), [#131](https://github.com/ngrok/kubernetes-ingress-controller/pull/131), [#137](https://github.com/ngrok/kubernetes-ingress-controller/pull/137)
- Minimum TLS Version Route Module [#125](https://github.com/ngrok/kubernetes-ingress-controller/pull/125)
- Webhook Verification Route Module [#122](https://github.com/ngrok/kubernetes-ingress-controller/pull/122)
- Add/Remove Header Route Module [#121](https://github.com/ngrok/kubernetes-ingress-controller/pull/121)
- Add IP Policy CRD and IP Policy Route Module [#120](https://github.com/ngrok/kubernetes-ingress-controller/pull/120)
- Load certs from the directory `"/etc/ssl/certs/ngrok/"` for ngrok-go if present [#111](https://github.com/ngrok/kubernetes-ingress-controller/pull/111)

### Fixed
- Fix bug from Driver and Store refactor so ingress status has CNAME Targets for custom domains updated correctly [#162](https://github.com/ngrok/kubernetes-ingress-controller/pull/162)
- Reduce domain controller reconcile counts by not updating domains if they didn't change  [#140](https://github.com/ngrok/kubernetes-ingress-controller/pull/140)
- Remove routes from remote API when they are removed from the ingress object [#124](https://github.com/ngrok/kubernetes-ingress-controller/pull/124)

## 0.3.0
### Changed
- Renamed docker image from `ngrok/ngrok-ingress-controller` to `ngrok/kubernetes-ingress-controller`.
- Added new controllers for `domains`, `tcpedges`, and `httpsedges`.
- Updated go dependencies
- Moved `main.go` to root of project to match what `kubebuilder` expects.
- Updated `Makefile` to match what `kubebuilder` currently outputs.
- Created `serverAddr` flag and plumbed it through to `ngrok-go`
- Read environment variable `NGROK_API_ADDR` for an override to the ngrok API address.

## 0.2.0
### Changed

- Moved from calling ngrok-agent sidecar to using the ngrok-go library in process.

## 0.1.X

### Initial Alpha Releases

The ngrok ingress controller is currently in alpha. Releases will have varying features with breaking changes.
