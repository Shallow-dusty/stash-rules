# Stash Rules

Personal Stash rules for an overseas-by-default network environment:

- LAN and private networks: `DIRECT`
- Mainland China domains and IPs: `DIRECT`
- Everything else: continue through the existing Mihomo/Stash configuration

The override deliberately contains no `MATCH` rule, proxy nodes, subscription
URLs, or policy-group names.

## Install on iOS

Open this URL on the iPhone or iPad that has Stash installed:

<https://link.stash.ws/install-override/raw.githubusercontent.com/Shallow-dusty/stash-rules/main/stash/cn-direct.stoverride>

Enable the imported override in Stash and reload the active configuration.

## Files

- `stash/cn-direct.stoverride`: one-time remote override installed in Stash
- `rules/cn-direct-domain.yaml`: domain rule set updated automatically by Stash

Stash checks the remote domain rule set hourly. To publish changes, edit the
rule file and push to `main`; no reinstallation is required.

## Safety

This repository must contain rules only. Never commit proxy subscriptions,
node credentials, UUIDs, API keys, private hostnames, or Tailscale addresses.
