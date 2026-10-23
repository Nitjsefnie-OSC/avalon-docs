# Names and Handles

**Status:** Planned — non-unique labels and domain-proven identity handles are the decided model; the current node-local name rules remain described below.

A display name is an untrusted label; the identity id identifies the account. Decisions [#1125](https://github.com/avalon-initiative/avalon-protocol/issues/1125) and [#1215](https://github.com/avalon-initiative/avalon-protocol/issues/1215) put trust and uniqueness in domain-proven handles, with short id fingerprints alongside labels. This page distinguishes that direction from the current name lookup.

## Labels and fingerprints

Planned: display names are non-unique, self-chosen labels. Clients show a label beside a short id fingerprint and use a verified-handle badge to distinguish a domain-proven name. A lookalike label does not establish that two accounts are the same identity.

Decision [#1215](https://github.com/avalon-initiative/avalon-protocol/issues/1215) drops protocol-level cross-shard name-conflict renaming and id-lookalike name restrictions. Per-node uniqueness may remain as a local user-interface constraint. Neither that constraint nor an id chosen to win a name contest makes a label trusted.

## Domain-proven handles

Planned: a handle is a domain name, such as `alice.example`, proven in both directions:

- The identity profile claims the domain name.
- A well-known record on the domain names the identity id.

Lookup verifies those directions with a short cache, rather than relying on a one-time stored proof: domains can change hands. Handles can be revoked, replaced, or lost while the identity id stays the same. Public resolution maps a handle to an identity id without a session or a ledger scan. These verification and resolution rules are tracked in [#1317](https://github.com/avalon-initiative/avalon-protocol/issues/1317).

A hoster may issue handles under its domain. An identity that moves can claim another handle, so a handle does not bind the account to that hoster. A trusted handle proves the domain-to-identity relationship; the profile remains [self-described metadata](./identity.md#self-described-metadata-is-self-expression-not-fact).

## Current names and discovery

The current implementation uses `display_name` for the lookup called a handle in `GET /friends/handle/{handle}`. Registration rejects a taken name locally, and cross-shard projection can store a conflicting name with an id suffix. Those node-local rules are described in [identity](./identity.md#names-across-nodes); they do not establish network-wide ownership of a display name.

The current name-search and people-discovery routes require a session. Opt-in label search remains distinct from planned public handle resolution; see [social graph](./social-graph.md#handles-and-discovery) and decision [#1125](https://github.com/avalon-initiative/avalon-protocol/issues/1125).

## Implementation

Status: Planned for network-wide identity handles ([avalon-protocol#1317](https://github.com/avalon-initiative/avalon-protocol/issues/1317)). The existing per-node domain-proven name claims do not implement that identity-handle model. See [shard names](./network-trust-anchors/shard-identity-and-names.md#domain-proven-names) for their current proof and conflict rules; the identity-handle plan instead requires verification at lookup as domains change hands.

## Related

- [Identity](./identity.md), [social graph](./social-graph.md), [guilds](./guilds.md)
- [Committed objects](./committed-objects.md), [permanence and redaction](./permanence-and-redaction.md)
- [Privacy](./privacy.md)
