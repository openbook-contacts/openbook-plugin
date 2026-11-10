---
name: import-a-spreadsheet
description: Import contacts into Openbook from a spreadsheet, a CSV, an Excel file, a Google Sheets link, a PDF roster, an email group's subscriber export or a pasted table: finding the table in every tab, mapping its columns, sorting people into groups by column or section, setting who sees what first, and checking the contacts with the person before adding anyone.
---

# Import a spreadsheet or roster

Use this when the person gives you rows of people: a team roster, a class roster, a staff directory, a sign-up form's export, a Google Group's or groups.io group's subscriber export, or a table pasted into the chat. For a photo or a scan, follow `import-from-a-photo` instead.

## 1. Decide where they go

- Call `my_access`. Ask which directory and group the people go in, or offer to start one: `create_organization` with a `name` for a club, school or company, or without one for a group of the person's own in Personal, like Book Club.
- Importing a whole file takes being an owner of the directory (`import_contacts`), which the person always is in Personal. Someone with add access who isn't an owner adds people one at a time with `add_contact`, and an add of a mobile number the directory already has waits for an owner.
- **A roster from an email group,** like a groups.io or Google Group subscriber export: it's that email group's people. Set `email_group` to the email group's address on the group, like maplecourt@groups.io, confirming it with the person, and say what Founding Member is, as `import-from-email` does, without promising it. Then follow `import-from-email`'s rules for who sees what and its last step, helping people join.

## 2. Find the table

- **A Google Sheets link:** open it with this app's own access to their Google Drive, if they added one. Otherwise ask them to download it (File, Download, as Microsoft Excel or CSV) and attach the file here.
- **Several tabs or sheets:** list each with how many rows it has and what it seems to hold, and ask which to import. A tab for each team or class is a group each; a tab like Payments or Schedule usually isn't people.
- **The header row isn't always the first.** Skip titles, blank rows and notes above it, and find the row that names the columns. Further down, skip a header repeated for a printout's next page, totals and blank rows.
- **A PDF roster:** read its text as a table, page by page; one that's only a picture follows `import-from-a-photo`.

## 3. Read the columns

Map each column to a field and show the person the mapping before going on:

- **Name:** one name per contact, joining first and last name columns, “Hana Sato”. “Sato, Hana” is “Hana Sato”. A name for two people, like “Hana & Ken Sato”, is two contacts, each with their own number or email where the row has them; ask when two people share one number.
- **Phone:** label each number `mobile`, `home` or `work`, from the column's name (Cell and Mobile are `mobile`). Only mobile numbers identify a person, so ask about a column just called Phone. Split a cell with two numbers, like “415-555-0148 / 415-555-0149”, and ask what each is.
- **Email, address, company, title, birthday, website** (`url`): as their columns say.
- **A column that sorts people,** like Team, Grade, Role or Committee: offer a group for each value, named for who's in it, like Coaches and Parents, or U10 Parents.
- **A column for each group,** like Choir, Ushers and Greeters with an X or Yes where someone's in it: a group for each column, and each person in every group they're marked in.
- **A section for each group:** a row with only a heading, like “U10” or “Sopranos”, and people under it, puts everyone under it in that group, until the next heading.
- **A row for a family,** like Parent 1, Parent 2 and Student: make a contact for each person with their own number or email, and offer a note everyone in the group reads, like “Parent of Ava (U10)”.
- **Columns that aren't contact details,** like paid, shirt size or allergies: leave them out unless the person asks for them as notes, and say that notes are read by everyone the group's Notes rule shows them to.

## 4. Check every value

- US numbers work in any format; numbers outside the US need their country code, like +44. One number Openbook can't read refuses the whole call, so look at each one first and ask about any that look short, long or mistyped.
- Never make up a missing number or email: leave the field out.
- Rows with the same mobile number are one person: merge them, keeping each group they belong in, and the same for a person on two tabs.

## 5. Set who sees what, before adding

A new group shows only Notes until its rules are set; every other field is Hidden from everyone but owners. Ask what people in each group should see of each field, Visible, Request required or Hidden, and set it with the group: `rules` on `create_organization`, or on `manage_groups` `create` or `update`, keyed like `phone.mobile`, `phone.home`, `email` and `address.home`.

## 6. Confirm

Show the count, the groups, the rules and a few rows, and anything left out and why: “I found 42 people on two tabs: 30 parents and 12 coaches, 41 with a mobile number. I'll create Riverside FC with Parents and Coaches, with mobile numbers visible in each. I skipped the Payments tab. Shall I add them?”

## 7. Import

- `import_contacts` with the group and up to 500 contacts a call; split a bigger file and keep going until every row is in. For several groups, import each group's people into it. Someone in two groups with a mobile number goes in with both imports, the second joining the contact the first made; someone without one goes in once, then `manage_groups` `add_contacts` puts them in the other group (`search_contacts` finds them).
- A contact's `note` in `import_contacts` or `add_contact` is one only the importer sees. For a note everyone in the group should read, call `add_note` for that contact after the import.
- An organization's free plan holds 1,000 contacts and 5 groups. A person keeps up to 5 groups of their own in Personal, My Contacts and By Request not counting. If Openbook refuses for a limit, say what it is and, for an organization, point to withopenbook.com, never a price.

## 8. Report and next steps

Say how many were added, how many joined contacts the directory already had, how many of those got details they didn't have (`filled`), and anything refused. Then offer to invite them (`invite-people`, with `add_to_group: false`, since they're in the group now) or to give them the group's Share page (`share_page` in `my_access`), with its QR code and invite link, and say that each person gets the group on their phone by joining.
