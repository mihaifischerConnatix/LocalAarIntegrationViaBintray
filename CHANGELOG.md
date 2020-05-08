# Changelog for Open Measurement SDK on Android

## 1.3.1 - 2019-01-21
- Add fix and unit tests.
- Use new API for creating configs.

## 1.3.0 - 2019-12-17

OM SDK 1.3 is a signficant update.  It adds support for some key new use cases for OMID 1.3 while allowing scripts using OMID 1.2 to run correctly.  Integrations (apps and SDKs) using OM SDK will need to make code changes.  See the [Migration Guide](docs/migration.md) for details.

### Changed
The following features changed their API from OM SDK 1.2 to 1.3.  The old 1.2 APIs are still functional but obsolete in this release; they will be deprecated in OM SDK 1.3.2 and removed in 1.3.4.

- Method `Omid.activateWithOmidApiVersion(omsdkVersion, applicationContext)` replaced by `Omid.activate()`
- Method `AdSessionContext.createNativeAdSessionContext()` added `contenturl` parameter
- Method `AdSessionContext.createHtmlAdSessionContext()` added `contenturl` parameter
- Method `AdSessionConfiguration.createAdSessionConfiguration()` added `creativeType` and `impressionType` parameters
- Method `AdSession.addFriendlyObstruction()` added `purpose` and `detailedReason` parameters
- Method `VideoEvents.loaded(vastProperties)` replaced by `AdEvents.loaded(vastProperties)`
- Class `VideoEvents` replaced by `MediaEvents`
- Package `omid.library.adsession.video` replaced by `omid.library.adsession.media`

### Added

- Method `AdSessionContext.createJavaScriptAdSessionContext()`
- Method `AdEvents.loaded()` added no-argument overload

### Obsolete
The following feature is still present but obsolete in OM SDK 1.3.0.  It will be deprecated in OM SDK 1.3.2 and removed in 1.3.4.

- Method `Omid.isCompatibleWithOmidApiVersion()`

## 1.2.22 - 2019-12-01
- Increased destruction timeout delay for internal WebViews of native AdSessions to give verification scrips time to process events for very short ad sessions.
- Native changes for JS fix to handle resource level access mode & verification params properly 

## 1.2.21 - 2019-11-11
- Update version to match JS and iOS SDKs; no changes from 1.2.20

## 1.2.20 - 2019-09-30
- Update version to match JS and iOS SDKs; no changes from 1.2.19

## 1.2.19 - 2019-09-10
- Update to accurately report 'hidden' or 'notFound' for non visible ad views and include geometry.
  Must use with OMSDK JS 1.2.18 or above.
  
## 1.2.18 - 2019-08-29
- Update version to match JS and iOS SDKs; no changes from 1.2.17

## 1.2.17 - 2019-07-22
- Ensure initial hierarchy event is published. 

## 1.2.16 - 2019-06-24
- Update version to match JS and iOS SDKs; no changes from 1.2.15

## 1.2.15 - 2019-05-24
- Fix CI, Upgrade gradle versions & move global version values into a 'versions' file

## 1.2.13 - 2019-03-22
- Update version to match JS and iOS SDKs; no changes from 1.2.12.

## 1.2.12 - 2019-02-13
- Remove @deprecated JavaDoc

## 1.2.11 - 2019-01-23
- Update version to match JS and iOS SDKs; no changes from 1.2.8.

## 1.2.8 - 2018-12-05
- Update version to match JS and iOS SDKs; no changes from 1.2.7.

## 1.2.7 - 2018-11-27
- Update version to match JS and iOS SDKs; no changes from 1.2.6.

## 1.2.6 - 2018-11-01
###  Update 
- Method 'Omid.activateWithOmidApiVersion()' no longer checks for compatibility with the passed in API version number.

## 1.2.5 - 2018-10-10
- Update docs and comments to use "OM SDK" consistently.

## 1.2.4 - 2018-08-29
- Update version to match JS and iOS SDKs; no changes from 1.2.3.

## 1.2.3 - 2018-08-17
- Update version to match JS and iOS SDKs; no changes from 1.2.2.

## 1.2.2 - 2018-08-02
- Update version to match JS and iOS SDKs; no changes from 1.2.1.

## 1.2.1 - 2018-07-18
- Update version to match JS and iOS SDKs; no changes from 1.2.0.

## 1.2.0 - 2018-07-03
- Update version to match JS and iOS SDKs; no changes from 1.1.4.

## 1.1.4 - 2018-06-20
- Update version to match JS and iOS SDKs; no changes from 1.1.3.

## 1.1.3 - 2018-05-30
### Update
- Update Android docs with information about potential side-effects.

## 1.1.2 - 2018-05-08
- Update version to match JS and iOS SDKs; no changes from 1.1.1.

## 1.1.1 - 2018-04-24
### Fixed
- Add timeouts to make OmidBridgeTest pass more reliably.

## 1.1.0 - 2018-03-29
- First General Availability release of OM SDK for Android.
