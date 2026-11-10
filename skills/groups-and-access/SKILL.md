---
name: groups-and-access
description: Run groups in Openbook: create, rename and delete groups, set what everyone in a group sees (Visible, Request required or Hidden), give people access and group permissions, choose who can invite, pick a group's QR color, see the activity log, and move a group of the person's own into an organization.
---

# Groups and access

Each part takes its own permission, and owners hold them all. `my_access` says what the person holds in each group.

## Groups

- **Create:** `manage_groups` `create` with the `directory`, a `name` for who's in it, and `rules`. It takes Create groups in that directory; whoever creates a group gets every permission on it. A new group shows only Notes until its rules are set.
- **How it looks** and **What people see:** `manage_groups` `update` with `name` and `color` (How it looks), and `rules`, `delivery` (`synced` to phones, or `lookup`, found only in this app) and `peer_grants_allowed` (whether people who see a field can say yes to a request for it), which take What people see.
- **Field rules:** keyed like `phone.mobile`, `email` or `note`, each `visible`, `request` or `hidden`. When a change closes a field, the result's `still_see` names who still sees it more openly, through their own overrides or another group, since the most open rule wins. Tell the person.
- **Who's in:** `manage_groups` `add_contacts` and `remove_contacts`. Removing never deletes: a contact out of every group waits in its directory's Missing Group.
- **Delete the group:** `manage_groups` `delete` removes the group with its access and invites, and deletes none of its contacts. A directory's last group can't be deleted.

## Access

- **Who has access:** `manage_access` `list` with the `group` shows each person with access, their user ID and what they can do there, for people with Give access. Use it to find someone before changing their access.
- `manage_access` `give`, `change` or `remove`, per person per group: everyone with access views the group, and `access` adds `add`, `edit` and `delete`, and the group permissions `give_access` (Give access), `whos_in` (Who's in), `join_and_find` (Who can join and find it), `what_people_see` (What people see), `how_it_looks` (How it looks), `share_with_group` (Share with the group) and `delete_group` (Delete the group). A key left out is off when giving and stays as it is when changing. It takes Give access, and nobody gives more than they hold.
- `overrides` are field rules for one person in one group, replacing the group's rule for them; only owners open a field the group hides.
- With `directory` and `create_groups`, owners let someone create groups there.

## Inviting and joining

`manage_groups` `update`, with Who can join and find it: `anyone_can_invite` (everyone with access can invite), `auto_approve` (people asking to join get in without waiting) and `add_from_links` (people who join from an invite link or the QR code are added to the group as contacts too). Some of these take a plan to turn off.

## The QR photo

Each group's cards on iPhones show its QR photo, the code of the person's invite link that others scan to ask to join, in one look every group shares, on the group's color. People with How it looks change only its `color`, a hex code like #0B6870: show `preview_qr_photo` with the color first, then `manage_groups` `update`. Openbook refuses colors phones couldn't scan, saying why. Anything more, like a logo or a picture, is a look of its own that Openbook's team sets up: say to write to support@withopenbook.com. `qr_on_cards: false`, which takes a plan, shows contacts' own photos on cards instead.

## Owners

- `manage_owners` adds or removes owners; `transfer_ownership` hands over the organization; `leave_organization` steps down.
- `update_directory` renames a directory, whose name starts every one of its groups on phones; `update_organization` renames the organization, which phones never show.
- `activity_log` shows who changed what, through which app.
- `move_to_organization` moves a group of the person's own, from Personal, into an organization they own, with its contacts, access and invites; it can't move back, so confirm.

Hide from search, `qr_on_cards: false` and growing past the free plan's 25 users, 5 groups or 1,000 contacts take a plan: say so and point to withopenbook.com, never a price.
