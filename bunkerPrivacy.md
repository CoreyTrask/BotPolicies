---
title: Privacy Policy
---
> **Last Updated:** 20 October 2026

# Bunker Defence - Privacy Policy

## 1. Introduction
This Privacy Policy explains how **Bunker Defence** ("the Bot", "we", "us") processes, stores, and protects data in compliance with the UK General Data Protection Regulation (UK GDPR) and the Data Protection Act 2018.

Our lawful basis for processing data under Article 6(1)(f) of the UK GDPR is **Legitimate Interests**—specifically, protecting Discord communities and their members from fraud, phishing, malware distribution, and account takeover attacks.

## 2. Data Collection & Processing
We adhere strictly to the principle of data minimisation. **Normal, benign messages and images are evaluated in volatile memory (RAM) only and are never written to our database.**

### A. Transient In-Memory Processing (Not Stored)
* **Message & Image Evaluation:** When a message is posted in a protected channel, the Bot inspects the text, URLs, and image attachments in memory using local Optical Character Recognition (OCR), QR decoding, and perceptual hashing (`pHash`). If the message scores below the enforcement threshold, all extracted data is immediately discarded.
* **Velocity & Raid Tracking:** To detect rapid multi-channel or cross-server spam raids, the Bot temporarily holds message timestamps, Server/Channel/Message IDs, and a non-reversible MD5 content hash in memory for up to **45 seconds**, after which they are automatically purged.

### B. Persistent Data (Stored Only on Security Events or Configuration)
Persistent data is stored in our local database (`bunker_defence_v3.db`) only in the following circumstances:
* **Security Incident Logs (`incidents`):** When a message triggers enforcement (`>= 60%` confidence), we log a unique Incident ID, Server ID (`guild_id`), Author User ID (`user_id`), a truncated snippet of the flagged message (up to 500 characters), extracted OCR/QR text (up to 500 characters), matched threat patterns, confidence score, moderation action taken, and UTC timestamp.
* **Role Backups (`role_backups`):** When a compromised member's roles are backed up prior to a kick, ban, or quarantine, we store their User ID, Server ID, a JSON list of their assignable Role IDs, the associated Incident ID, and the timestamp so their roles can be automatically restored when they rejoin.
* **Server Configuration (`guild_config` & `exempt_channels`):** Stores the Server ID, configured Alert Channel ID, exempted Staff Channel IDs, and server-specific preferences (`critical_action`, `auto_restore_roles`, `dm_on_kick`).
* **Custom Blacklist Subscriptions (`identifiers` & `rule_subscriptions`):** When a moderator adds a custom scam signature, we store the pattern, vector type, weight, moderator notes, Server ID, and the submitting moderator's User ID (`added_by`) for audit and global review purposes.

## 3. Data Usage
Collected data is used exclusively for:
* Detecting, removing, and mitigating scam messages, malicious files, and spam raids across protected Discord servers.
* Displaying incident breakdowns and audit logs to Server Moderators via alert embeds and `/bunker logs`.
* Automatically restoring a member's previous server roles once they recover a compromised account and rejoin the server.
* Allowing moderators to mark false positives and calibrate signature weights.

## 4. Local Image Processing & Third-Party Requests
* **100% Local OCR & Image Inspection:** All OCR (`RapidOCR` / ONNX Runtime), QR code detection, and perceptual image hashing (`pHash`) are executed **locally on our host server**. User images and messages are **never** transmitted to external third-party AI services.
* **Shortlink Unfurling:** When a message contains a known URL shortener (e.g., `bit.ly`, `tinyurl.com`), the Bot may perform an automated HTTP `HEAD` request to resolve the destination domain against our phishing blacklist. No user identifiers are transmitted during this check.

## 5. Data Storage and Retention
All persistent data is stored securely in a local SQLite database (`bunker_defence_v3.db`) alongside rotating operational log files (`bunker_defence.log`, capped at 3 MB with a maximum of 2 backup files).

* **In-Memory Queues:** Velocity tracking records expire automatically within **30 to 45 seconds**.
* **Role Backups:** Completed role backups (`restored = 1`) are automatically purged after **90 days** by the Bot's automated maintenance task.
* **Incident Logs & Configurations:** Server incident logs and configurations are retained while the Bot operates in the server to provide moderators with historical audit trails (`/bunker status` and `/bunker logs`), or until a deletion request is submitted.

## 6. Data Deletion, Portability, and User Rights
Under the UK GDPR, you have the right to access, rectify, port, or request the erasure of your personal data:
* **False Positive Remediation:** If your message was flagged in error, any server moderator can click the **`🛡️ Mark False Positive`** button on the incident alert (or run `/bunker restore`), which updates the incident record, lifts active timeouts, and restores backed-up roles.
* **Data Access & Erasure Requests:** To request a copy of data associated with your Discord User ID or Server ID, or to request its permanent deletion from `bunker_defence_v3.db`, please contact the bot administrator.

## 7. Security
We implement strict technical and organisational measures to protect stored data, including restricted host environment access, local-only database bindings, SSRF network filtering, and role-based Discord permission checks on all administrative commands.

## 8. Changes to this Policy
We may update this Privacy Policy periodically to reflect improvements to the Bot or changes in legal requirements. Updated versions will be published on this page with a revised "Last Updated" date.

## 9. Contact
For data privacy enquiries, subject access requests, or data deletion requests under UK GDPR, please contact the bot administrator (Discord: `corey.t`) or the owner of the server where the Bot is deployed.
