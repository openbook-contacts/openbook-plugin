---
name: import-from-a-photo
description: Add contacts to Openbook from photos or scans: a handwritten sign-up sheet, a printed roster, a whiteboard, a stack of business cards or a screenshot, several photos in one running table, headings on a page as groups, reading every entry carefully, asking about anything hard to make out, and confirming before adding.
---

# Import from a photo or scan

Use this when the person hands you pictures of people's details. Spreadsheets and PDFs with real text follow `import-a-spreadsheet`.

1. **Where they go.** Call `my_access` and agree on the directory and group, or start one (`create_organization`, or `manage_groups` `create`). Set the group's field rules before adding anyone: a new group shows only Notes until they're set.
2. **Read every entry exactly as written.** Copy names and numbers character by character. Never guess a digit or a letter: list each one you can't make out and ask, one question at a time, “Is Ruth Park's (415) 555-0148 or (415) 555-0143?”. Leave out a field the person can't confirm rather than adding a wrong one.
3. **Read the page as it's meant.** A photo taken sideways, upside down or at an angle reads the right way up. A page cut off at an edge, blurry or in shadow: say which part you can't read, like “the last column on the right”, and ask for another photo of it rather than guessing. Read two columns on a page, and both sides of a sheet, in order.
4. **Know what you're reading.**
   - A sign-up sheet: the heading often says what people signed up for, which can name the group, like Choir or Snack Rota. Crossed-out rows are out.
   - Business cards: the name, company, title, work phone (`work`), a mobile only where the card marks one (M, Cell or Mobile), the email and the website (`url`). The card's picture isn't the person's photo: never add it as one.
   - A screenshot of a group chat or a contacts screen: take only what it shows, and ask before adding people who only appear in someone else's message.
5. **Headings make groups.** A page with sections, like Sopranos, Altos and Tenors, or U10 and U12, offers a group for each, with the people under each heading in it. Tell the person they can take a picture of each page or section to add its group.
6. **Several photos:** keep one running table across them, and merge entries with the same mobile number, including one that shows in two overlapping photos.
7. **From an email group,** like a printed groups.io subscriber list: set `email_group` to the email group's address on the group, confirming it with the person, and say what Founding Member is, as `import-from-email` does, without promising it.
8. **Confirm** with a table of everyone you read, saying which values the person confirmed for you: “I read 18 names and 17 mobile numbers from 3 photos. Add all 18 to Grace Church • Choir?”
9. **Add.** Owners use `import_contacts`, up to 500 a call; anyone else with add access uses `add_contact` for each person, where a mobile number the directory already has waits for an owner. One number Openbook can't read refuses the whole call, so check them first.
10. **Report** how many were added and anything left out, then offer to invite them (`invite-people`) or give them the group's Share page (`share_page` in `my_access`) to show its QR code.
