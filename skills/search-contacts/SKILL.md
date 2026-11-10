---
name: search-contacts
description: Find someone among the contacts the person can see in Openbook: by name, role, team or anything in their notes, like "who drives on Saturdays" or "the U10 coach", open their card, and ask for a number or email their group keeps behind a request.
---

# Search the person's contacts

Use this first whenever someone asks for a person, a number or “who…”. If the person isn't among their contacts, offer `find-through-people-you-know` or `ask-my-contacts`.

1. **Search everything first:** `search_contacts` with `query`, a name or a few words from what they know, like “snack rota”, “goalkeeper” or “tennis pro”, and no `group` or `directory`: a role, a team or a note can be on someone in any group. It matches word by word, in names, the fields and notes the person sees and group names, best matches first. Filter by `group` or `directory` from `my_access` only when the person names one, and never conclude someone isn't there from a filtered search. To list everyone, leave `query` out; `*` or “all” does the same. Follow `cursor` for more than `limit`.
2. **Open a card:** `get_contact` returns the fields the person sees, and lists the fields they can ask for (`requestable`) without their values.
3. **Ask for a field they can't see:** each requestable field comes with `can_ask`, the people who can say yes, people in the group who see it and owners. Show the person those names and let them pick; there's no default. Then `request_field` with the `contact`, the `field` (like `{ type: "phone", label: "mobile" }`), `ask` with the picked users, and a `reason` in their words, which the people asked read.
4. **A field the contact doesn't have:** `get_contact` may list it in `missing_fields_from_others`, with `could_share`, people the person knows who have the same mobile number in their own contacts; ask them with `request_field` the same way.
5. **Follow up:** `my_requests` shows what they asked and the answers. An answer shows on the card, and on their phones at the next sync.
6. **A wrong detail:** `update_contact` if they can edit the contact, or else `suggest_change`, picking who to send it to.
7. **Notes:** `add_note` adds to a contact's notes, which everyone the Notes rule shows them to reads; `notes_only_you` keeps one nobody else reads.
8. **Owners** also find contacts in no group (`ungrouped: true`) and in Recently Deleted (`recently_deleted: true`); see `tidy-contacts`.

On an iPhone or iPad, groups the person keeps only in search don't show in their Contacts lists, but searching in Contacts finds their contacts.
