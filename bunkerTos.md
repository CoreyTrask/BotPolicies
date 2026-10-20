---
title: Terms of Service
---
> **Last Updated:** 20 October 2026

# Bunker Defence - Terms of Service

## 1. Introduction
Welcome to **Bunker Defence** ("the Bot"). By inviting, configuring, or interacting with the Bot within any Discord server, you agree to be bound by these Terms of Service. If you do not agree to these terms, please do not invite or use the Bot.

## 2. Applicable Law
These Terms of Service shall be governed by and construed in accordance with the laws of the United Kingdom. Any disputes arising under or in connection with these terms shall be subject to the exclusive jurisdiction of the UK courts.

## 3. Service Description & Automated Moderation
Bunker Defence is an automated cybersecurity and moderation utility designed to protect Discord communities from phishing links, malicious attachments, image-based scams (via Optical Character Recognition, perceptual hashing, and QR code inspection), and coordinated spam raids.

By deploying the Bot in your server, you acknowledge and authorise the Bot to:
* Inspect message text, forwarded message snapshots, embeds, and image attachments in non-exempt channels.
* Automatically delete messages that meet or exceed the configured threat confidence threshold.
* Automatically apply temporary timeouts (quarantine), strip assignable roles, kick, or ban accounts (including compromised moderator accounts positioned below the Bot's role hierarchy) when critical threat thresholds are reached.
* Back up a removed member's assignable server roles and send an automated account-recovery Direct Message (where enabled) so their roles can be restored upon rejoining.

## 4. Acceptable Use & Blacklist Submissions
Server Administrators and Moderators may add custom signatures to their server's local blacklist and submit patterns for global review via `/bunker add` or the `🛡️ Report Scam to Bot` context menu.

* **Prohibited Behaviour:** You agree not to misuse the Bot. Prohibited actions include attempting to exploit, reverse-engineer, overload, or disrupt the Bot's OCR or heuristic engine; intentionally submitting benign words or false patterns to disrupt global or local blacklists; or using the Bot in violation of Discord's Terms of Service or Community Guidelines.
* **Access Termination:** We reserve the right to revoke access to the Global Review Queue or blacklist any user or server from using the Bot at our sole discretion if abuse or malicious activity is detected.

## 5. Age Requirements
By using the Bot, you confirm that you meet the minimum age of digital consent in your country (e.g., 13+ in the UK) as required by Discord's Terms of Service. We do not knowingly collect data from individuals under this age.

## 6. Availability, False Positives & Modifications
The Bot is provided on an "as is" and "as available" basis without warranties of any kind.
* While the Bot uses multi-signal corroboration to minimise false flags, no automated security system is infallible. Neither the Bot nor its developers guarantee that every malicious message will be intercepted or that legitimate messages will never be flagged.
* Server Administrators are responsible for configuring appropriate alert channels (`/bunker setup`), channel exemptions (`/bunker exempt`), and role hierarchies, as well as reviewing incident alerts using the built-in false-positive remediation tools.
* We reserve the right to updatethreat signatures, modify features, or suspend the Bot at any time without prior notice.

## 7. Limitation of Liability
To the fullest extent permitted by applicable UK law, the developers and maintainers of the Bot shall not be liable for any direct, indirect, incidental, consequential, or punitive damages arising out of your use of or inability to use the Bot, including but not limited to damages resulting from missed scam payloads, false-positive moderation actions, or loss of server roles.

## 8. Changes to Terms
We may update these Terms of Service from time to time. Continued use of the Bot after any changes constitutes your acceptance of the revised Terms.

## 9. Contact
If you have any questions or concerns regarding these Terms of Service, please contact the bot administrator (Discord: `corey.t`).
