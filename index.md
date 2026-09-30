---
layout: default
title: Streamloom Privacy Policy
---

# Privacy Policy for Streamloom

**Last Updated: 28 September 2026**

SoftArchium ("we", "us", or "our") builds and maintains **Streamloom**, a live television and media streaming player application for Android devices (phones, tablets, and Android TV / Google TV).

This Privacy Policy explains how Streamloom handles user information. Our core architectural principle is **privacy by design**: we collect no personal data, require no accounts, and never track you individually. We do send anonymous, aggregate usage counts — see Section 3C for what these are and why — but nothing about them can be tied back to your device or to you. In most regions, a small baseline of that (that the app was opened, and when a stream fails to play) is always sent, so we can keep the service reliable; a separate Settings toggle controls everything beyond that baseline. In the European Economic Area, the United Kingdom, Switzerland and a small number of nearby countries, that baseline is controlled by the same Settings toggle instead, like everything else; in mainland China, we send no usage statistics of any kind. See Section 3C for exactly which regions and why.

---

## 1. Information We Do Not Collect

Streamloom does not collect, transmit, store, or sell any personally identifiable information (PII). Specifically:

* **No User Accounts**: Streamloom requires no account creation, sign-up, email address, phone number, password, or profile information.
* **No Device Identifiers**: We do not collect or access Android Advertising IDs (AAID), hardware serial numbers, IMEI, MAC addresses, or persistent device identifiers.
* **No Location Data**: We do not collect GPS, cellular, Wi-Fi, or network location data. The app does not ask where you are or what language you speak, and reads neither.
* **No Advertising or Profiling**: Streamloom contains no third-party advertising SDKs, tracking pixels, behavioral analytics engines, or attribution libraries.
* **No Third-Party Analytics**: Streamloom contains no third-party analytics SDK from an outside vendor. The anonymous, first-party usage statistics described in Section 3C below are a different thing: a count sent to our own server, never to a third party.

---

## 2. Information Stored Locally on Your Device

To provide essential media player functionality, Streamloom stores certain preferences locally on your device:

* **Favourites**: Channels you choose to bookmark.
* **Watch History**: Which channels you have played, and when. Recorded on the device; no screen reads it back yet.
* **App Settings**: Your chosen catalogue language and playback preferences.

**All local data resides exclusively in your device's private application sandbox (a Room database and DataStore preferences, readable only by Streamloom under Android's per-app storage isolation). This information is never transmitted to SoftArchium or any third party, and is excluded from cloud backups.**

---

## 3. Network Communications & Diagnostics

When you use Streamloom, the app makes network requests strictly to deliver media content and maintain app stability:

### A. Media Streaming and Channel Catalogue
* **Catalogue**: Streamloom fetches channel lists, stream URLs, categories, countries and — when you open a channel — its programme data over HTTPS from our Supabase project, and the catalogue from an Upstash Redis cache that holds a copy of it. Every request is anonymous: none carries an account, a device identifier, or a request body describing you.
* **Media Streams**: Playback streams are loaded directly from the URLs in the catalogue. Media3 ExoPlayer contacts the stream host directly, so that host sees your IP address in the same way any website you visit does.
* **Channel Logos**: Station logos are loaded and cached locally on your device via Coil image loader directly from public CDN endpoints.

### B. Anonymous Crash Reports and Performance Diagnostics (Sentry)
To ensure application stability and resolve software crashes across fragmented Android hardware:
* If configured, Streamloom utilizes Sentry to record anonymous technical crash reports.
* **What is sent**: Stack traces; Android OS version, app version and device model; the device context Sentry collects by default — memory, storage, battery, connection type, locale and screen orientation; playback error codes and the failing file extension; and, when a catalogue sync fails, the stage it failed at and the exception's class name.
* **What is NEVER sent**: User identities, stream URLs (which can carry access tokens), catalogue error messages (which can quote a request URL or a row of the response), search queries, or personal files.
* **About IP addresses**: Streamloom never attaches your IP address to a crash report, and never uses one to infer your location. Like any service your device contacts, Sentry's servers see the address a report arrives from. We do not use it, and we do not link it to anything.

### C. Anonymous Usage Statistics
Streamloom sends anonymous counts of how the app is used to our own server, to help us see which streams and searches are working and how fast the app is for people. Gathering some usage data is standard practice among free and ad-supported streaming services; we run no ads, so this is how we keep the service both free and reliable.

**A small baseline is always sent in most regions, and is not affected by the Settings toggle below there**: that the app was opened (bucketed to "first time today / this week / this month / ever", never a date that identifies your device); and, when a stream fails to play, which channel and which stream it was (identified only by a one-way scrambled version of its address, never the address itself) and the general category of what went wrong (for example, a server error or a playback/codec problem) — never a failure caused by your own network connection. Every request, of any kind, also carries the app's version number, so we can tell which build an issue affects. This baseline is the minimum we need to know the service is being used and that something needs fixing; none of it is personal, none of it is tied to an account (there are none), and none of it can single out your device.

**Where this baseline is different: the EEA/UK/Switzerland/nearby countries, and China.** If your device is in the European Economic Area, the United Kingdom, Switzerland, or a small number of nearby countries whose laws treat this the same way, the baseline above is controlled by the Settings toggle like everything else — turning it off stops it too. If your device is in mainland China, we do not send any usage statistics at all, of any kind, and the toggle has no effect either way. Which of these applies is worked out entirely on your device — from your network or SIM country, or your device's language/region setting where there is no telephony hardware, such as on a TV — and is never itself sent to us or stored anywhere.

**Settings → Detailed Usage Statistics**, on by default, controls everything beyond that baseline (and, in the EEA/UK/Switzerland/nearby-countries case above, the baseline itself). Turn it off and the app also stops sending: which channels are played and for roughly how long, in coarse time ranges; whether the guide was opened; whether a search came up empty; and how fast the catalogue, the guide, and video playback started, in coarse ranges rather than exact timings. Turning it off stops all of this immediately, including anything already queued; turning it back on does not resend what was cleared.

* **What is NEVER sent, whether the toggle is on or off**: The text of anything you search for; a stream's actual web address; your device's advertising ID, a serial number, or any other persistent identifier that could single out your device or you; your IP address or exact location — our server can tell only the country and, sometimes, the broader region a request came from, the same way it can for every request this app makes (including simply loading the channel catalogue), and we never see, store, or use the address itself once we have that; and the exact time of anything, only which coarse range it fell into.
* **How this differs from a third-party analytics SDK**: This code is ours, and the server it reports to is ours — there is no outside analytics company in the loop, nothing is sold, and nothing is used to build a profile of you or to target advertising.

The auditable version of this list is kept with the app's source code and is available on request at the address in Section 8. If the two ever differ, that one is correct.

---

## 4. Third-Party Services and External Links

Streamloom plays streams from third-party media sources listed in a public, community-maintained catalogue. SoftArchium does not operate, endorse, control, or monitor those streaming servers. When you play a channel, your device communicates directly with the respective third-party server, subject to that third party's privacy practices.

The services SoftArchium does operate are **Supabase** (the catalogue database) and **Upstash** (a cache holding a copy of the same catalogue). Both are data processors holding public catalogue data — no account, no identifier, and no record of what you watch. Like every server your device contacts, they see the address a request comes from; we do not use it or link it to anything.

---

## 5. Children's Privacy

Streamloom does not knowingly collect or solicit personal information from children under the age of 13 (or under 16 in certain jurisdictions). Because the application collects no personal information, there is no personal data of a child — or of anyone else — for us to hold, process, or disclose.

Note that the catalogue includes channels from many countries and Streamloom does not classify their content; the app is not designed or directed at children.

---

## 6. Data Retention and Deletion

Because Streamloom does not operate user accounts or store personal data on remote servers, SoftArchium maintains no server-side user records to retain or delete.

* **To delete all local data**: You can remove all favourites, history, and cached data at any time by clearing the app data in Android Settings (`Settings → Apps → Streamloom → Storage & cache → Clear storage`), or by uninstalling the application.

---

## 7. Changes to This Privacy Policy

We may update this Privacy Policy from time to time to reflect changes in our practices or regulatory requirements. Any updates will be posted to this page with an updated "Last Updated" date.

---

## 8. Contact Us

If you have questions, feedback, or concerns regarding this Privacy Policy or our privacy practices, please contact us:

* **Developer / Organization**: SoftArchium
* **Email**: `support@softarchium.com`
