---
name: tidy-contacts
description: Tidy an Openbook directory: find duplicate contacts and merge them, sort out the directory's Missing Group, bring back a contact from Recently Deleted (30 days), and approve or decline adds of mobile numbers the directory already has.
---

# Tidy a directory

Most of this is for owners, who see every contact, Missing Group and Recently Deleted; anyone else tidies what their own access reaches.

## Duplicates

Openbook keeps one contact per mobile number in a directory, so duplicates are the same person under two numbers, an email, or none.

1. `search_contacts` across the directory (`directory`, `limit` 100, following `cursor`), and list pairs with the same email or a very close name and no conflicting mobile number.
2. Show each pair side by side, and ask which to keep.
3. Merge: `update_contact` gives the one kept any values it's missing, `manage_groups` `add_contacts` puts it in the other's groups, then `delete_contact` sends the extra one to Recently Deleted, where it can be brought back for 30 days. Notes stay with the contact they're on, so say so before deleting one that has some.

## Missing Group

`search_contacts` with `ungrouped: true` lists contacts in no group. Each waits there until someone puts it in a group (`manage_groups` `add_contacts`) or deletes it (`delete_contact`). Ask about each, or groups of them.

## Recently Deleted (30 days)

`search_contacts` with `recently_deleted: true` lists what was deleted, when each goes for good and the groups it left. `manage_groups` `add_contacts` with a group brings one back into it. An owner deleting one that's already there deletes it for good at once: confirm that twice.

## Adds waiting for an owner

When someone who isn't an owner adds a mobile number the directory already has, it waits. `review_adds` `list` shows them, and `approve` or `decline` answers each, with the contact and group it names.

Removing and deleting are different: say “take out of the group” for a removal, and “delete” only for `delete_contact`.
