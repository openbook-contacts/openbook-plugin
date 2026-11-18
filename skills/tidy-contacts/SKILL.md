---
name: tidy-contacts
description: Tidy an Openbook directory: find every likely duplicate in one call and merge the ones the person confirms in another, sort out the directory's Missing Group, bring back a contact from Recently Deleted (30 days), and approve or decline adds of mobile numbers the directory already has.
---

# Tidy a directory

Most of this is for owners, who see every contact, Missing Group and Recently Deleted; anyone else tidies what their own access reaches.

## Duplicates

Openbook keeps one contact per mobile number in a directory, so duplicates are the same person under two numbers, an email, or none. Find and merge them in about two calls, and one question:

1. `search_contacts` with `directory` and `duplicates: true` (`limit` up to 500) lists every pair that may be one person, each with its reasons, the same email, number or name, from the values the person sees. `import_contacts` reports the same for what it just added, as `possible_duplicates`.
2. Show all the pairs in one message, each with which you'd keep (the older one, or the one with more on it) and why, and ask once: “These 9 look like the same person twice. Merge them, keeping the first of each?” Name any with notes, since both contacts' notes end up on the one kept.
3. One `merge_contacts` call with every pair they said yes to, `pairs: [{ keep, other }]`: the one kept takes each value of the other's it doesn't have, both emails when they differ, its groups and its notes, and the other goes to Recently Deleted, where it can be brought back for 30 days. A contact someone was given, shared or asked for details of can't be merged away, so keep that one instead.

## Missing Group

`search_contacts` with `ungrouped: true` lists contacts in no group. Each waits there until someone puts it in a group (`manage_groups` `add_contacts`) or deletes it (`delete_contact`). Ask about each, or groups of them.

## Recently Deleted (30 days)

`search_contacts` with `recently_deleted: true` lists what was deleted, when each goes for good and the groups it left. `manage_groups` `add_contacts` with a group brings one back into it. An owner deleting one that's already there deletes it for good at once: confirm that twice.

## Adds waiting for an owner

When someone who isn't an owner adds a mobile number the directory already has, it waits. `waiting_adds` shows them, and `review_adds` `approve` or `decline` answers each, with the contact and group it names.

Removing and deleting are different: say “take out of the group” for a removal, and “delete” only for `delete_contact`.
