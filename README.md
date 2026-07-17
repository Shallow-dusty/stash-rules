# Stash Rules

Personal Stash rules for an overseas-by-default network environment:

- LAN and private networks: `DIRECT`
- Mainland China domains and IPs: `DIRECT`
- Everything else: continue through the existing Mihomo/Stash configuration
- Optional Tailscale addresses and `*.ts.net`: a separate, locally authenticated
  `Tailscale` node

The overrides deliberately contain no `MATCH` rule, subscription URLs, account
credentials, auth keys, assigned Tailscale IPs, or private MagicDNS suffixes.
Their routing responsibilities do not overlap:

- `cn-direct.stoverride` deliberately leaves `100.64.0.0/10` and
  `fd7a:115c:a1e0::/48` unmatched.
- `tailscale.stoverride` exclusively owns those Tailscale ranges and `*.ts.net`.

## Install on iOS

Open this URL on the iPhone or iPad that has Stash installed:

<https://link.stash.ws/install-override/raw.githubusercontent.com/Shallow-dusty/stash-rules/main/stash/cn-direct.stoverride>

To add Tailscale access, install this second override:

<https://link.stash.ws/install-override/raw.githubusercontent.com/Shallow-dusty/stash-rules/main/stash/tailscale.stoverride>

Enable both overrides and reload the active configuration. They are
non-overlapping, so their relative order in the Stash override list does not
affect routing.

Reload the active configuration, long-press the `Tailscale` proxy, open
`Tailscale Authentication`, and complete interactive authentication once.

## Files

- `stash/cn-direct.stoverride`: one-time remote override installed in Stash
- `stash/tailscale.stoverride`: optional Tailscale node and routing override
- `rules/cn-direct-domain.yaml`: domain rule set updated automatically by Stash

Stash checks the remote domain rule set hourly. To publish changes, edit the
rule file and push to `main`; no reinstallation is required.

## Safety

Never commit proxy subscriptions, node credentials, UUIDs, API keys, auth keys,
assigned Tailscale addresses, or private MagicDNS suffixes. Standard Tailscale
protocol ranges and an unauthenticated generic node declaration are allowed.
