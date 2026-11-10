---
name: import-a-vcard-file
description: Import a vCard file (.vcf) into an Openbook group: a List or All Contacts exported from Contacts on an iPhone or Mac, a Google Contacts or Outlook export, or a card someone shared, keeping names, numbers, emails, addresses, birthdays and more under the group's field rules, with the file's notes kept as notes only the person sees.
---

# Import a vCard file into a group

Use this when the person attaches a `.vcf` and wants its people in a group: an organization's group, like a team's Contacts List becoming Riverside FC • Parents, or a group of their own in Personal. To keep their own contacts in Openbook as their address book, or share them with someone, follow `host-your-contacts`, which uses these steps. For Find people through contacts, which takes only names, numbers and emails, follow `add-phone-contacts`.

## 1. Where they go

Call `my_access`, agree on the group, and set its field rules first: a new group shows only Notes until they're set, and everyone with access sees what the rules show. Importing takes being an owner of the directory, as the person is of their own groups; with add access alone, add people one at a time with `add_contact`.

## 2. Getting the file

- iPhone: in Contacts, tap Lists, hold the List (or All Contacts), choose Export, tap the check mark, and send it here.
- Mac: in Contacts, select the List or the contacts, then File, Export, Export vCard.
- Google Contacts or Android: Export, as a vCard. Outlook: export contacts.

## 3. Reading it

A file holds one card per person, from `BEGIN:VCARD` to `END:VCARD`.

- **Lines:** a line that starts with a space or a tab continues the line before it. A backslash escapes a comma, a semicolon or another backslash, and `\n` is a new line.
- **Name:** `FN`, or else `N`'s parts (family;given;middle;prefix;suffix) as “given middle family suffix”. A card with neither, like a company's, takes `ORG` as its name.
- **Phones (`TEL`):** CELL, MOBILE and IPHONE are `mobile`; HOME `home`; WORK and MAIN `work`. Skip FAX and PAGER. A custom label sits on its own line in the same group, like `item1.TEL` with `item1.X-ABLabel`; Apple's own labels read like `_$!<Mobile>!$_`, so take what's between `<` and `>`, in lowercase. Only mobile numbers identify a person.
- **Emails (`EMAIL`):** HOME `home`, WORK `work`, or the custom label.
- **Addresses (`ADR`):** the parts after the first two (street;city;region;postal code;country) joined with commas, `home` or `work`.
- **Others:** `ORG` is `company`, `TITLE` is `title`, `BDAY` is `birthday` (a date like 1985-03-04, or --03-04 with no year), `URL` is `url`, and `X-SOCIALPROFILE` or `IMPP` is `social`.
- **Photos (`PHOTO`):** base64 after `ENCODING=b`, or a `data:` address. A photo is a field Openbook keeps as each group's rule for Photo says, Hidden until set. Photos make a file large, so ask before including them.
- **Notes (`NOTE`):** what the person wrote about someone for themselves. Put it in the contact's `note` in `import_contacts`, which only they see, never anyone else, owners included. Never send it as a field or with `add_note` unless they ask for others to read it.
- **Leave out** Openbook's own cards, whose names end with a group, like “Hana Sato • Coaches”, or read “Openbook”, and cards that are only a List (`X-ADDRESSBOOKSERVER-KIND:group`).

## 4. Check and confirm

- Merge cards with the same mobile number: the same person exported from two accounts.
- One number Openbook can't read refuses the whole call; numbers outside the US need their country code.
- Show the count, the group, the fields you'll import, what you left out and why, and a few cards, then wait for a yes.

## 5. Import and report

- `import_contacts` with up to 500 contacts a call, fewer when photos are in.
- A card whose mobile number the directory already has joins that contact in the group and fills in what it doesn't have yet: each field it has no value for, a photo if it has none, and the person's note if they keep none on it. It never changes or removes what's there, its name included, so a changed number or email still takes `update_contact`.
- Report how many were added, how many joined contacts already there, and how many of those got details they didn't have (`filled`).
