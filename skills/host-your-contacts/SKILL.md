---
name: host-your-contacts
description: Keep the person's own contacts in Openbook as their address book, with addresses, birthdays and their own notes, on their phones and kept in sync both ways, and share it with someone they trust, a partner, a spouse or a close colleague, as a contact book they keep up to date together.
---

# Host your contacts in Openbook, and share them

Two things people want, often together:

- **Openbook as their address book:** their contacts, with every detail, in a group of their own in Personal, on their phones, where edits on the phone come back to Openbook.
- **A shared contact book:** that group shared with someone they trust, who sees what its rules show and, with edit access, keeps it up to date with them.

## 1. Choose the group

- **A new group of their own** (`create_organization` without a `name`, with a `first_group` like Contacts, or Family & Friends for one to share) holds exactly the contacts they bring in. Best for sharing, since they choose who's in it.
- **My Contacts**, if they've added contacts with Find people through contacts, holds those people already, with names, numbers and emails only. An import matches them by mobile number and fills in what each doesn't have yet, like an address or a birthday, never changing what's there.

A person keeps up to 5 groups of their own, My Contacts and By Request not counting.

## 2. Set what others see

As the group's owner, the person sees every field whatever its rules. The rules decide what anyone they share it with sees: for a shared contact book, suggest Visible for phone, email, address and birthday (`rules` like `phone.mobile`, `email`, `address.home`, `birthday`). Set them before importing.

## 3. Explain requests from others

Before importing, say it plainly: nobody sees their contacts; people they know can ask them for one of these contacts, and nothing is shared without their yes. What the group's rules show, like a contact's job title, company, city and shared notes, can help people they know find someone through them, never with a name or a number. To keep one contact out, `hide_contacts`; to keep the whole group out of everyone else's searches, Hide from search, which takes a plan (point to withopenbook.com, never a price). Notes only they see are never used.

## 4. Bring the contacts in

Follow `import-a-vcard-file` with their exported All Contacts, or a List of it. Their notes from the file go in as notes only they see. Ask before including photos.

## 5. Put it on their phones

Their own groups start hidden: show this one with `update_settings` `groups`, its ID and `shown: "in_contacts"` (or `set-up-phones` if Openbook isn't on their phone yet).

- Their phone shows Openbook's cards beside its own for the same people. Openbook never changes or deletes the phone's own contacts. If they later want Openbook's to be the only copy, that's theirs to do in their phone's own account once they've checked everything came through; never do it for them or tell them to rush it.
- Edits to Openbook's cards on the phone come back to Openbook. A contact they make on an iPhone inside one of Openbook's Lists joins that group; one made in Openbook's account outside any List waits in Personal • Missing Group.

## 6. Share it

`invite_users` with the group, the person's name and their mobile number or email, and `add_to_group: false` unless they should be a contact in it too.

- Pick their access in the invite: viewing only, or `add` and `edit` to keep it up to date together, and `delete` if they should remove contacts. To change it later, `manage_access` `list` shows who has access and their user IDs, then `change` with the person and the new access.
- They see it by its name, like Family & Friends, or My Contacts as the person's, like “Maya's Contacts”, and only what its rules show. They can't see the person's notes only they see.
- Openbook is invite only for now, so the invite is also how someone new gets in.

Confirm each step before doing it.
