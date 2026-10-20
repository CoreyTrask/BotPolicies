---
title: Privacy Policy
---
> **Last Updated:** 20 October 2026

# Bunker Defence - Privacy Policy

## 1. Introduction
This Privacy Policy explains how **Bunker Defence** ("the Bot", "we", "us") processes, stores, and protects data in compliance with the UK General Data Protection Regulation (UK GDPR) and the Data Protection Act 2018.

Our lawful basis for processing data under Article 6(1)(f) of the UK GDPR is **Legitimate Interests**, specifically, protecting Discord communities and their members from fraud, phishing, malware distribution, and account takeover attacks.

## 2. Data Collection & Processing
We adhere strictly to the principle of data minimisation. **Normal, benign messages and images are evaluated in volatile memory (RAM) only and are never written to our database.**

### A. Transient In-Memory Processing (Not Stored)
- **Message & Image Evaluation:** When a message is posted in a protected channel, the Bot inspects the text, URLs, and image attachments in memory using local Optical Character Recognition (OCR), QR decoding, and perceptual hashing (`pHash`). If the message scores below the enforcement threshold, all extracted data is immediately discarded.
- **Transient Image Hash Cache:** To prevent repeated OCR processing during multi-server image raids, a non-reversible SHA-256 digest of recently inspected images and their extracted text is cached in volatile RAM (capped at 512 entries) and is cleared automatically as new images are processed or when the Bot restarts.
- **Velocity & Raid Tracking:** To detect rapid single-channel, multi-channel, or cross-server spam raids, the Bot temporarily holds message timestamps, Server/Channel/Message IDs, and a non-reversible MD5 content hash in memory for up to **45 seconds**, after which they are automatically purged.

### B. Persistent Data (Stored Only on Security Events or Configuration)
Persistent data is stored in our local database (`bunker_defence.db`) only in the following circumstances:
- **Security Incident Logs (`incidents`):** When a message triggers enforcement (`>= 60%` confidence), we log a unique Incident ID, Server ID (`guild_id`), Author User ID (`user_id`), a truncated snippet of the flagged message (up to 500 characters), extracted OCR/QR text (up to 500 characters), matched threat patterns, confidence score, moderation action taken, and UTC timestamp.
- **Role Backups (`role_backups`):** When a compromised member's roles are backed up prior to a kick, ban, or quarantine, we store their User ID, Server ID, a JSON list of their assignable Role IDs, the associated Incident ID, and the timestamp so their roles can be automatically restored when they rejoin.
- **Server Configuration & Trust Status (`guild_config` & `exempt_channels`):** Stores the Server ID, configured Alert Channel ID, exempted Staff Channel IDs, server protection preferences (`critical_action`, `auto_restore_roles`, `dm_on_kick`), and network anti-sabotage metadata (`trust_status`, strike counters, and `blacklist_reason`).
- **Custom Blacklist Subscriptions & Votes (`identifiers`, `rule_subscriptions` & `false_positive_votes`):** When a moderator adds a custom scam signature or marks an incident as a false positive, we store the pattern, vector type, weight, moderator notes, Server ID, Incident ID, and the moderator's User ID (`added_by` / `user_id`) to prevent duplicate voting and audit global proposals.

## 3. Data Usage
Collected data is used exclusively for:
- Detecting, removing, and mitigating scam messages, malicious files, and spam raids across protected Discord servers.
- Displaying incident breakdowns and audit logs to Server Moderators via alert embeds and `/bunker logs`.
- Automatically restoring a member's previous server roles once they recover a compromised account and rejoin the server.
- Allowing moderators to mark false positives, calibrate local signature weights, and corroborate global scam signatures while preventing network sabotage.

## 4. Local Image Processing & Third-Party Requests
- **100% Local OCR & Image Inspection:** All OCR (`RapidOCR` / ONNX Runtime), QR code detection, and perceptual image hashing (`pHash`) are executed **locally on our host server**. User images and messages are **never** transmitted to external third-party AI services. Embedded images are fetched strictly via Discord's official CDN/proxy servers.
- **Shortlink Unfurling:** When a message contains a known URL shortener (e.g., `bit.ly`, `tinyurl.com`), the Bot may perform an automated HTTP `HEAD` request to resolve the destination domain against our phishing blacklist. No user identifiers are transmitted during this check.

## 5. Data Storage and Retention
All persistent data is stored securely in a local SQLite database (`bunker_defence.db`) with restricted host file permissions (`0600`) and an automated rolling hot backup (`bunker_defence_backup.db`), alongside rotating operational log files (`bunker_defence.log`, capped at 3 MB with a maximum of 2 backup files).

- **In-Memory Queues:** Velocity and rate-limit tracking records expire automatically within **30 seconds to 15 minutes**.
- **Automatic Deletion on Server Removal:** If the Bot leaves or is removed from a Discord server, all server-specific operational data, including incident logs, role backups, channel exemptions, false-positive votes, and uncorroborated local blacklist rules, is **automatically and immediately deleted**. (If a server was blacklisted or flagged for platform abuse, only its numeric Server ID, trust status, strike counters, and blacklist reason are retained to prevent abuse evasion).
- **90-Day Automated Pruning:** For active servers, both security incident logs (`incidents`) and completed role backups (`role_backups` where `restored = 1`) older than **90 days** are automatically purged every 6 hours by the Bot's maintenance task.

## 6. Data Deletion, Portability, and User Rights
Under the UK GDPR, you have the right to access, rectify, port, or request the erasure of your personal data:
- **False Positive Remediation:** If your message was flagged in error, any server moderator can click the **`🛡️ Mark False Positive`** button on the incident alert (or run `/bunker restore`), which updates the incident record, lifts active timeouts, and restores backed-up roles.
- **Right to Erasure (User & Server Data Deletion):** You may request a copy of your data or the permanent deletion of all data associated with your Discord User ID or Server ID at any time by contacting the bot administrator. Bot administrators have dedicated erasure commands (`/bunker_admin purge_user` and `/bunker_admin purge_server`) that permanently purge all incident records, role backups, and votes linked to a User ID or Server ID and anonymise any rule subscription metadata. Requests are fulfilled within **one calendar month (30 days)** in accordance with UK GDPR.
- **Supervisory Authority:** If you are dissatisfied with how your data is handled, please contact the bot administrator first so we can resolve your concern. You also have the right under the UK GDPR to lodge a complaint with the UK Information Commissioner's Office (ICO) at [ico.org.uk](https://ico.org.uk).

## 7. Security
We implement strict technical and organisational measures to protect stored data, including restricted host file permissions (`0600`), local-only database bindings, SSRF and decompression-bomb filtering, and role-based Discord permission checks on all administrative commands.

## 8. Changes to this Policy
We may update this Privacy Policy periodically to reflect improvements to the Bot or changes in legal requirements. Updated versions will be published on this page with a revised "Last Updated" date.

## 9. Contact
For data privacy enquiries, subject access requests, or data deletion requests under UK GDPR, please contact the bot administrator (Discord: `corey.t`) or the owner of the server where the Bot is deployed.
