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
- **Private Contacts** (`private_contacts: true` in `my_access`), if they've added contacts with Find people through contacts, holds those people already, each whole, with everything their phone has. It fills only through `add-phone-contacts`: sending their contacts again brings in new ones and what changed, and `import_contacts` never takes it.

A person keeps up to 5 groups of their own, Private Contacts and By Request not counting.

## 2. Set what others see

As the group's owner, the person sees every field whatever its rules. The rules decide what anyone they share it with sees: for a shared contact book, suggest Visible for phone, email, address and birthday (`rules` like `phone.mobile`, `email`, `address.home`, `birthday`). Set them before importing.

## 3. Explain requests from others

Before importing, say it plainly: nobody sees their contacts; people they know can ask them for one of these contacts, and nothing is shared without their yes. What the group's rules show, like a contact's job title, company, city and shared notes, can help people they know find someone through them, never with a name or a number. To keep one contact out, `hide_contacts`; to keep the whole group out of everyone else's searches, Hide from search, which takes a plan (point to withopenbook.com, never a price). Notes only they see are never used.

## 4. Bring the contacts in

For a new group of their own, follow `import-a-vcard-file` with their exported All Contacts, or a List of it: their notes from the file go in as notes only they see, and ask before including photos. For Private Contacts, follow `add-phone-contacts`, which takes the whole file, photos and notes included.

## 5. Put it on their phones

A new group of their own shows on their phones from the start. Private Contacts starts hidden, since it holds the contacts already on their phone: show it with `update_settings` `groups`, its ID and `shown: "in_contacts"`. Check `shown` in `my_access` either way, and use `set-up-phones` if Openbook isn't on their phone yet.

- Their phone shows Openbook's cards beside its own for the same people. Openbook never changes or deletes the phone's own contacts. If they later want Openbook's to be the only copy, that's theirs to do in their phone's own account once they've checked everything came through; never do it for them or tell them to rush it.
- Edits to Openbook's cards on the phone come back to Openbook. A contact they make on an iPhone inside one of Openbook's Lists joins that group, and one made in Openbook • Private Contacts joins Private Contacts while it shows; one made outside any List waits a day, then goes to their Missing Group, in Openbook • Personal Groups.

## 6. Share it

`invite_users` with the group, the person's name and their mobile number or email, and `add_to_group: false` unless they should be a contact in it too.

- Pick their access in the invite: viewing only, or `add` and `edit` to keep it up to date together, and `delete` if they should remove contacts. To change it later, `group_access` shows who has access and their user IDs, then `manage_access` `change` with the person and the new access.
- They see it by its name, like Family & Friends, or Private Contacts as the person's, like “Maya's Private Contacts”, and only what its rules show. They can't see the person's notes only they see.
- Openbook is invite only for now, so the invite is also how someone new gets in.

Confirm each step before doing it.
