---
title: Support policy for the Warehouse Management mobile app
description: Learn about the support policies that apply to the Warehouse Management mobile app, including the V3 end-of-support milestone in May 2026 and the rolling 12-month support window for version 4 and all later releases that starts on May 1, 2027.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.topic: conceptual
ms.date: 04/28/2026
ms.custom:
  - bap-template
---

# Support policy for the Warehouse Management mobile app

This article describes the support policies that apply to the Warehouse Management mobile app. Two distinct policies apply, depending on which version your devices run:

- **Version 3 (V3)** reaches its official end of support in May 2026. After that milestone, Microsoft no longer accepts support cases related to the V3 client software. Migrate devices to V4 before May 2026 to maintain support coverage.
- **Version 4 (V4) and all later releases** follow a rolling 12-month support window that begins on May 1, 2027. After that date, a release is eligible for support cases only if its publication date is within the 12 months that precede the date when the support case is opened. This policy applies to V4 and to every subsequent release of the app, regardless of whether that release is a major, minor, or patch version.

These policies are essential to ensure the quality, security, performance, and platform compatibility of the Warehouse Management mobile app. By focusing engineering and support investment on a current set of releases, Microsoft can deliver timely security updates, address platform-level changes from Apple, Google, and Microsoft, and provide a consistent troubleshooting baseline. Investigating issues against legacy or out-of-window releases would slow the delivery of these improvements and dilute the protections that warehouse operations depend on.

The app continues to function regardless of release age. These policies define the scope of support case intake, not service availability or the ability to sign in.

## Version 3 support policy

As announced in the [Migration to V4 Guide](warehouse-app-migrating-from-v3-v4.md), version 3 (V3) of the Warehouse Management mobile app reaches its official end of support in May 2026. Migrate devices to V4 before that date to maintain support coverage.

V3 is based on the *Xamarin* framework, which is no longer supported, so Microsoft can't provide any new features or bug fixes for V3.

### Scope of support after May 2026

Back-end APIs remain compatible with V3 during the migration window so that V3 clients can continue to operate while customers transition to V4. The duration of this back-end compatibility isn't guaranteed and may end as Supply Chain Management services evolve.

- **No new releases** – Microsoft can't build, patch, or release updates for V3 because the underlying Xamarin framework is deprecated.
- **Support cases** – Microsoft support teams no longer accept or investigate support cases related specifically to the V3 client software.

Devices that remain on V3 after May 2026 follow the V3 support policy described in this section. The 12-month rolling window described later in this article applies to V4 and all later releases only; it doesn't apply to V3.

### Examples of out-of-scope scenarios

The following list provides examples of issues that Microsoft no longer investigates for V3.

- **Authentication and identity (Microsoft Entra ID)** – V3 uses legacy authentication libraries that Microsoft no longer maintains.
    - **Unsupported** – Failures related to modern Microsoft Authentication Library (MSAL) flows, *Device not compliant* errors, and new conditional access policies enforced by Microsoft Entra ID.
    - **Resolution** – Migrate to V4 to use current and secure authentication protocols.

- **Client-side performance and connectivity** – The networking stack and libraries within V3 are frozen at their current versions.
    - **Unsupported** – Issues regarding local latency, connection drops, or timeouts originating from the outdated client-side libraries.
    - **Note** – If a performance issue is verified to be a server-side or service-wide latency issue, Microsoft continues to investigate it as part of standard cloud service support.

- **Operating system (OS) compatibility** – Because Apple (iOS) and Google (Android) continually release new operating system versions, legacy apps often encounter breaking changes.
    - **Unsupported** – Crashes, UI glitches, or failure to launch on mobile OS versions released after the final V3 release.
    - **Resolution** – Continued compatibility is only guaranteed for the V4 application, which is built on the latest software development kits (SDKs).

## Version 4 and later support policy

Starting **May 1, 2027**, version 4 (V4) and every later release of the Warehouse Management mobile app follow a rolling 12-month support window. At any time on or after May 1, 2027, a release is eligible for support cases only if its publication date is within the previous 12 months relative to the date the support case is opened. The same rolling 12-month rule applies to every release that Microsoft publishes from V4 onward, regardless of whether it's a major, minor, or patch version.

### How publication date is defined

For the purposes of this policy, the publication date of a release is the date when the release first becomes available on Microsoft App Center. Subsequent availability on the Microsoft Store, Google Play, or the Apple App Store can occur later (especially on iOS, because of store review timelines), but the publication date that determines support eligibility is always the App Center release date. Each V4 and later release, starting from version 4.1.0.0, includes its publication date in [What's new or changed in the Warehouse Management mobile app](warehouse-app-whats-new.md).

### Examples

- A release that's published on **April 30, 2026** is eligible for support cases until **April 30, 2027**. Because that boundary falls before May 1, 2027, the release becomes ineligible for support cases on May 1, 2027 (the date the rolling window policy takes effect).
- A release that's published on **June 15, 2026** is eligible for support cases until **June 15, 2027**.
- A release that's published on **August 1, 2027** is eligible for support cases until **August 1, 2028**.

The window is evaluated on the date the support case is opened. There is no grace period beyond the 12-month boundary. Update the device to a release within the support window before opening a support case.

### Why the 12-month window matters

Limiting support to the most recent 12 months of releases is critical to maintain the quality, security, and reliability that warehouse operations depend on. It allows Microsoft to:

- Deliver timely security fixes and respond to vulnerabilities on a current code base, instead of backporting fixes across many legacy builds.
- Keep pace with platform-level changes from Apple, Google, and Microsoft (operating system updates, authentication libraries, and store policies) that often introduce breaking behavior in older releases.
- Diagnose issues against a known, well-tested baseline so that root-cause analysis is fast and accurate.
- Focus engineering investment on improvements that benefit all customers, rather than on issues that have already been resolved in newer releases.

### Scope of the 12-month window

- **Support cases** – Microsoft support teams accept and investigate support cases only when the affected device runs a V4 or later release whose publication date is within the previous 12 months. For older releases, you're asked to update to a supported version before a support case can be investigated.
- **Critical production outages** – Microsoft may still investigate severity-1 incidents that block widespread production operations, on a case-by-case basis. The standard guidance is to first update to a supported release. This exception isn't a substitute for keeping deployments current.
- **Preview builds** – Preview or beta builds distributed through Microsoft App Center are not part of the 12-month support window. Use preview builds only for evaluation; report issues through the [preview feedback channel](warehouse-app-whats-new.md).
- **App availability** – The app continues to run on devices regardless of the installed version. Microsoft doesn't deliberately block out-of-window clients, and back-end services don't reject their connections at the protocol level. However, Supply Chain Management services evolve over time, and older releases may eventually become incompatible with newer back-end behavior. Compatibility for out-of-window releases is not guaranteed.
- **Security and platform fixes** – Critical fixes are delivered in current releases. Devices that stay on older releases don't receive those fixes.

### How to identify the installed version

To identify the version of the Warehouse Management mobile app that's installed on a device, open the app and review the version information shown on the sign-in screen or in the app's **Settings** page. Compare that value to the publication dates listed in [What's new or changed in the Warehouse Management mobile app](warehouse-app-whats-new.md).

### How to stay within the support window

- Keep auto-update enabled in your app store, or schedule mass-deployment updates through Microsoft Intune or another mobile device management (MDM) solution. For details, see [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md).
- Track release dates in [What's new or changed in the Warehouse Management mobile app](warehouse-app-whats-new.md). Each V4 and later release, starting from version 4.1.0.0, is tagged with its release date.
- Plan a rollout cadence that updates devices at least once per year so that no installation drifts past the 12-month window.

## Related information

- [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md)
- [Migrate the Warehouse Management mobile app from V3 to V4](warehouse-app-migrating-from-v3-v4.md)
- [What's new or changed in the Warehouse Management mobile app](warehouse-app-whats-new.md)
- [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md)
