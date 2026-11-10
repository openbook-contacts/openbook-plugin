---
name: get-started
description: Set up Openbook right after installing it: see what the person can do, start a shared directory for their group from whatever they have (a spreadsheet, a photo, an email group, their coworkers' email), join one they were invited to, and put Openbook on their phone.
---

# Get started with Openbook

1. **See where they are.** Call `my_access`. It lists the directories and groups the person can act in. Everyone has their own directory, Personal.
2. **Ask what brought them.** They run a group, like a club, a class, a team or a company; they were invited to one; they want their own contacts kept in Openbook, or shared with a partner (`host-your-contacts`); or they want to find someone through people they know.
3. **Running a group:** ask what they have about who's in it, and use the import skill that fits:
   - a spreadsheet, a CSV, a Google Sheets link or a PDF roster: `import-a-spreadsheet`;
   - a vCard file, like a List exported from Contacts: `import-a-vcard-file`;
   - a photo of a sign-up sheet, a printed roster or business cards: `import-from-a-photo`;
   - an email group, like a Google Group, a groups.io group or a mailing list, or a reply-all thread: `import-from-email`;
   - the people they work with, at their company's email domain: `import-coworkers`;
   - the businesses and people their community recommends in its emails: `import-recommendations`;
   - nothing yet: start with a name and a first group, and add people as they come.

   When they bring an email group, say what it can bring, in these words: “If yours is the first group from this email group that 5 people join, your QR Card becomes a Founding Member card.” Never promise it (`founding-member`).

   Contacts live only in groups, so ask what to call its first group, for who's in it, like Parents, 1st Grade Teachers or Sales People, and what everyone in it should see of each field: Visible, Request required or Hidden. Confirm both, then `create_organization` with `name`, `first_group` and `rules`. Leaving out `name` makes a group of their own in Personal instead, like Book Club, which suits a few friends or a family.
4. **Invited to one:** they join from the invite link or the group's code, which asks for their mobile number and a texted code. Openbook is invite only for now, so that's the way in. Once they're in, `my_access` shows the group.
5. **Finding someone:** use `find-through-people-you-know`, which starts by adding the contacts on their phone (`add-phone-contacts`).
6. **On their phone:** `add_to_device` with `iphone`, `mac` or `android` returns the setup steps' link, which asks them to sign in on that device first. Give it as a link to open on that device. On an iPhone, they open it in Safari, sign in, then install the profile from Settings, and their groups appear in Contacts (`set-up-phones` has the rest).

Confirm every change with the person before making it.
