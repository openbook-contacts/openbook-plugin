---
name: refresh-a-group
description: Bring an Openbook group up to date from a new roster: a new season's team sheet, this year's class roster, a current staff export, showing who's new, whose details changed and who's no longer on it, and making only the changes the person approves.
---

# Refresh a group from a new roster

1. **Which group.** Call `my_access` and agree on the group. Read the new roster as in `import-a-spreadsheet` (or `import-from-a-photo` for a picture).
2. **Read what's there now:** `search_contacts` with the `group`, `limit` 100, following `cursor` until there's no more. Owners also check the directory's Missing Group (`ungrouped: true`), where people removed last season wait.
3. **Match people,** by mobile number first, then email, then the same name. Ask about near matches, like “Jon Lee” and “Jonathan Lee” with different numbers.
4. **Sort the changes into four:**
   - **New:** on the roster, not in the group. Someone waiting in Missing Group goes back with `manage_groups` `add_contacts`; anyone else is added (`import_contacts` as an owner, or `add_contact`).
   - **Changed:** a new number, email or address. An owner's import fills in only what a contact doesn't have yet, so a value that changed takes `update_contact`, which changes the contact everywhere it is in the directory, in every group, and takes edit access; without it, offer `suggest_change`.
   - **No longer on it:** `manage_groups` `remove_contacts` takes them out of this group, which takes Who's in. That isn't a delete: a contact out of every group waits in Missing Group, which only owners see, until someone puts it in a group or deletes it. Delete only when the person asks (`delete_contact`, which sends it to Recently Deleted for 30 days).
   - **The same:** leave them alone.
5. **Confirm each kind on its own,** with names: “6 new, 3 with a new number, 4 not on this year's roster. Add the 6, update the 3, and take the 4 out of U10 Parents?” The person may keep some who left, like coaches between seasons.
6. **Make the changes,** then report what was done and anything refused.
7. **Next:** offer to invite the new people (`invite-people`, `add_to_group: false`). People taken out of the group keep their own account; if they had access to the group, ask whether to remove it too (`manage_access` `remove`), since removing a contact doesn't change anyone's access.
