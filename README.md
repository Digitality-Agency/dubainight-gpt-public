# Dubai Night Reports

Install the Dubai Night reporting plugin in ChatGPT desktop. The package is public; report data is private and requires an approved Dubai Night reporting account.

This version connects to **staging data** for Dubai and Abu Dhabi. It provides articles, events, offers, venue pages, source URLs, recorded page views and CSV exports. Missing metrics are reported as unavailable.

## Install on desktop

You need ChatGPT desktop with plugin support, Git, and an approved reporting account. No GitHub account or repository permission is needed to download this public package.

Run these commands in Terminal:

```sh
codex plugin marketplace add https://github.com/Digitality-Agency/dubainight-gpt-public.git
codex plugin add dubainight-reports@dubainight-public
```

If `codex` is not on your Mac's PATH, use the executable bundled with ChatGPT:

```sh
/Applications/ChatGPT.app/Contents/Resources/codex plugin marketplace add https://github.com/Digitality-Agency/dubainight-gpt-public.git
/Applications/ChatGPT.app/Contents/Resources/codex plugin add dubainight-reports@dubainight-public
```

Open ChatGPT desktop, restart it if the new catalog is not visible, then open **Plugins** and find **Dubai Night Reports [Staging]**. Connect the reporting account, sign in through the browser, and approve read access. Return to desktop and start a new conversation.

If the connection prompt does not appear, start OAuth from Terminal:

```sh
codex mcp login dubainight-reports-staging
```

Use the same full executable path above if needed. Enter your password only on the reporting sign-in page, never in chat, commands or repository files.

Try:

> Generate an Amazonico Dubai report. Show article, event, offer and venue counts, recorded lifetime page views, and the top 5 articles with URLs. Clearly label staging data and unavailable metrics.

Then:

> Export the complete report as CSV and give me the browser download link.

CSV links may require another sign-in with the same account that created the report. Generate a fresh report if its link has expired.

## Workspace installation

A workspace administrator can use **Admin > Plugins > Add > Import marketplace** with this repository URL. Leave **Path** empty. Select a release commit or the default branch, then configure which members can install the plugin. The workspace import UI may still ask the administrator to connect GitHub even though this repository is public.

Users must separately sign in with an approved reporting account. Importing the package does not grant reporting access.

## Phone and web availability

ChatGPT currently marks plugins with bundled MCP servers as **Desktop only**, including remote HTTPS connections. This package does not provide mobile or web installation. See [OpenAI plugin management](https://learn.chatgpt.com/docs/enterprise/plugin-management).

## Record an installation demo

1. Show this public repository and its installation commands.
2. Add the catalog and install the plugin on desktop.
3. Open the plugin and complete the browser login and read-access consent, keeping the password hidden.
4. Start a new conversation and run the report prompt above.
5. Request the CSV export and show the actual downloaded file.

Use a fresh installation for a first-install video. An already installed and connected copy demonstrates reuse or reconnection instead.

## Updates

```sh
codex plugin marketplace upgrade dubainight-public
codex plugin add dubainight-reports@dubainight-public
```

Start a new conversation after updating. A previous development installation from a catalog named `personal` is a separate installation; avoid enabling both copies in the same conversation.

## What is public

This repository contains only the plugin manifest, public MCP endpoint and OAuth callback configuration, reporting skill, marketplace catalog and documentation. The service URL and loopback callback are public connection metadata, not secrets. Each installation uses public-client OAuth with PKCE and its own login; no shared client secret is distributed.

Backend code, database credentials, Firebase credentials, access rosters, reports, exports and deployment configuration are not distributed here. Backend authorization controls access for every reporting request. Installing or copying this package does not grant database access.

Maintainers must scan changes and Git history for secrets before publishing. Never add `.env` files, credentials, service-account keys or report data. Ignore rules help prevent mistakes but do not replace review.

[OpenAI plugin packaging and installation](https://developers.openai.com/plugins/build/plugins)
