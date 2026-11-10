---
name: set-up-phones
description: Put Openbook on the person's iPhone, iPad, Mac or Android phone with its setup link, list and remove their devices, choose which groups show in Contacts or only in search, and work out why a group or contact isn't on their phone.
---

# Openbook on phones

## Adding a device

1. `add_to_device` with `platform`: `iphone` (also for an iPad), `mac` or `android`. It returns the setup steps' link for that platform, which asks them to sign in on that device first, so it only ever adds a device to their own account.
2. Give the link as a link to open on that device itself.
   - iPhone or iPad: open it in Safari, sign in, tap to download the profile, then in Settings tap Profile Downloaded and Install. Their groups appear in Contacts.
   - Mac: open it in Safari, sign in and install the profile from System Settings. The file it downloads, Openbook.mobileconfig, signs in as them, so it's never for sending, and it can go in the Trash once installed.
   - Android: open it on the phone, sign in and tap Android under Add a phone or Mac.
3. Each device signs in as them, so a Mac's profile file is never for sending to anyone else.

## Seeing and removing devices

`my_devices` lists their phones, iPads and Macs and when each last synced. `remove_device` takes Openbook off one: its Openbook contacts leave it at its next sync, and the browser it was set up in is signed out of Openbook's pages.

## Which groups show

Each person picks, per group, with `update_settings` `groups` (each a `group` ID from `my_access` and `shown`):

- `in_contacts`: the group and its contacts' cards, shown as “Riverside FC • Parents”.
- `only_in_search`: off their phones; on an iPhone or iPad, searching in Contacts still finds its contacts.
- `hidden`, for their own groups in Personal only: off their phones and out of search too. Each of their own groups starts hidden; `personal_groups` shows or hides them all at once. By Request shows whenever it holds a contact someone shared.

Other settings: `directory_in_names`, where cards show a contact's groups (after the last name, after the first name, or off), and `keep_contact_photos`, contacts' own photos on cards instead of a group's QR code.

## When something's missing

- A group isn't there: check its `shown` in `my_access`; a group of their own starts hidden; a lookup-only group never shows on phones.
- A contact isn't there: they see contacts only through groups that show on phones; `search_contacts` finds them in the app either way.
- Changes reach phones at their next sync; `my_devices` says when each last synced.
