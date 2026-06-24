# The SCR Auto Scheduling Bot - Privacy Policy

## 1. Introduction
This Privacy Policy outlines how The SCR Auto Scheduling Bot ("the Bot", "we", "us") collects, uses, and protects user data in compliance with the UK General Data Protection Regulation (UK GDPR) and the Data Protection Act 2018.

## 2. Data Collection
We collect the minimum amount of data necessary to provide and maintain the Bot's functionality. The data collected includes:

* **User IDs:** Discord User IDs are collected to track requests, permissions, claims, economy balances, and user-specific settings.
* **Message IDs & Content:** Certain message IDs are tracked for persistent views, claims, and auto-deletion features. Message content is processed temporarily for command execution but is not stored long-term unless required for a specific persistent feature (e.g., active requests).
* **Server/Guild IDs:** Discord Server IDs are used to bind the Bot to configured guilds.
* **Timestamps:** Dates and times are logged for scheduling, cooldowns, reminders, and activity tracking.
* **Gambling/Economy Data:** Virtual balances, transaction history, stats, and achievements are stored for users participating in the Bot's economy features.
* **ClickUp Data:** Integration with ClickUp may involve processing task IDs, names, and linked data necessary for automated scheduling and syncing.

## 3. Data Usage
The collected data is used exclusively for:
* Providing the core functionalities of the Bot (e.g., request handling, scheduling, economy tracking).
* Persisting state across Bot restarts (e.g., saving active requests and claims).
* Enforcing role-based permissions and cooldowns.
* Improving and maintaining the Bot's performance and stability.

## 4. Data Storage and Retention
All persistent data is stored securely in local SQLite databases (`bot_database_*.db`).

* **Temporary Data:** Certain data, such as tracked Direct Messages or temporary active requests, are deleted automatically upon expiry or completion of their lifecycle.
* **Economy Data:** Gambling and economy data is retained as long as the user participates. Users can request deletion of this data via the `/deletegambledata` command provided to server administrators.
* **Logs:** Error logs and transient tracking tables (e.g., `sent_errors`) are periodically pruned (e.g., 30-day retention).

## 5. Data Deletion and User Rights
Under UK GDPR, you have the right to access, rectify, and erase your personal data.

* **Data Deletion:** To have your data deleted from the Bot's database, you can contact an administrator of the server where the Bot is active. Administrators have access to commands (e.g., `/deletegambledata`) that can purge specific user data. 
* Users can also opt-out of certain features or have their ongoing tracked requests cancelled/removed via standard bot interactions.

## 6. Data Sharing
We do not sell, rent, or share your personal data with third parties, except as strictly necessary to interact with designated third-party APIs (e.g., Discord API, ClickUp API, Google Sheets API) solely for the purpose of the Bot's advertised functionalities.

## 7. Security
We implement appropriate technical measures to protect the stored data, including local SQLite databases, standard file permissions, and limiting access to the host environment.

## 8. Changes to this Policy
We may update this Privacy Policy as necessary. Any significant changes will be communicated through documentation.

## 9. Contact
For data privacy concerns or to exercise your rights under UK GDPR, please contact the bot administrator (Discord: corey.t) or server owners where the Bot is deployed.
