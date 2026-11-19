---
name: set-up-phones
description: "Put Openbook on the person's iPhone, iPad, Mac or Android phone with its setup link, list and remove their devices, choose which groups show in Contacts or only in search, and work out why a group or contact isn't on their phone."
---

# Openbook on phones

## Adding a device

1. `add_to_device` with `platform`: `iphone` (also for an iPad), `mac` or `android`. It returns the setup steps' link for that platform, which asks them to sign in on that device first, so it only ever adds a device to their own account.
2. Give the link as a link to open on that device itself.
   - iPhone or iPad: open it in Safari, sign in, tap to download the profile, then in Settings tap Profile Downloaded and Install. Their groups appear in Contacts, under Lists, in four accounts (below).
   - Mac: open it in Safari, sign in and install the profile from System Settings. The file it downloads, Openbook.mobileconfig, signs in as them, so it's never for sending, and it can go in the Trash once installed.
   - Android: open it on the phone, sign in and tap Android under Add a phone or Mac.
3. Each device signs in as them, so a Mac's profile file is never for sending to anyone else.

## Where groups show on an iPhone, iPad or Mac

One profile adds four accounts, each listed under Lists in Contacts:

- **Openbook • Organization Groups**: every group of an organization they own, like “Riverside FC • Parents”, and its Missing Group. Someone who owns no organization sees it empty, and it fills once they make one, with nothing to install again.
- **Openbook • Shared by Others**: every group of an organization that they're in and don't own, By Request, and any organization's group they asked to join and are waiting on.
- **Openbook • Personal Groups**: their own groups, each by its name alone, like “Book Club”, the groups someone else made in their own directory that they're in, like “Maya’s Private Contacts”, their Missing Group, the Openbook card and their own card.
- **Openbook • Private Contacts**: everything they added with Find people through contacts, once they show it, as cards with no groups, each with its contact's own photo, and always the card Phone and Messages show for its number.

A phone or Mac added before Openbook had four accounts keeps the accounts it had, with anything for an account it lacks in the one it calls Openbook, so nothing leaves it; adding it again with `add_to_device` brings the four accounts and their names. Android shows every group in one list of labels.

## Seeing and removing devices

`my_devices` lists their phones, iPads and Macs and when each last synced. `remove_device` takes Openbook off one: its Openbook contacts leave it at its next sync, and the browser it was set up in is signed out of Openbook's pages.

## Which groups show

Each person picks, per group, with `update_settings` `groups` (each a `group` ID from `my_access` and `shown`):

- `in_contacts`: the group and its contacts' cards, shown as “Riverside FC • Parents”, or for a group of a person's own “Personal • Book Club”.
- `only_in_search`: off their phones; on an iPhone or iPad, searching in Contacts still finds its contacts.
- Their own groups in Personal take the same two. Each group of their own they create starts in Contacts, and Private Contacts starts only in search; `personal_groups` shows them all or keeps them all only in search at once. By Request shows whenever it holds a contact someone shared.

Other settings: `groups_on_cards`, whether cards show a contact's groups in its company, like “Acme Corp • Coaches” or “Coaches” (on by default; false leaves the contact's own company), and `keep_contact_photos`, contacts' own photos on cards instead of a group's QR code.

## When something's missing

- A group isn't there: check its `shown` in `my_access`; Private Contacts starts hidden, and a group of their own may have been hidden; a lookup-only group never shows on phones. On an iPhone, look under the account it belongs in (above).
- A contact isn't there: they see contacts only through groups that show on phones; `search_contacts` finds them in the app either way.
- Changes reach phones at their next sync; `my_devices` says when each last synced.
