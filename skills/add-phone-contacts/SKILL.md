---
name: add-phone-contacts
description: Bring the person's own phone contacts into Openbook with Find people through contacts: from an iPhone's exported All Contacts file, a Google Contacts, Mac or Outlook export, or numbers they paste, so people they know can ask them for someone, and they can find people through people they know.
---

# Add the contacts on their phone

Find people through contacts is how someone's own contacts come into Openbook. It's what lets them find people through people they know (`find-through-people-you-know`), and lets people they know ask them for a contact. It keeps each contact whole, every name, number, email, address, date, related name, profile, note and photo, in Private Contacts, whose history keeps what was sent for each. To make their contacts a group to share with someone, follow `host-your-contacts` instead.

1. **Explain first, in these terms:** nobody sees their contacts; people they know can ask them for one when they're looking for someone; nothing is shared unless they say yes. Their contacts go into Private Contacts, a group of their own that stays off their phones until they show it, its fields hidden from anyone they share it with until they open them. What they send passes through this app's provider on its way to Openbook.
2. **Get the file.**
   - iPhone: in Contacts, tap Lists at the top, hold All Contacts, choose Export, tap the check mark, then pick this app and send the file here.
   - Mac: in Contacts, select All Contacts, then File, Export, Export vCard.
   - Android or Google Contacts on the web: Export, as a vCard or a Google CSV.
   - Outlook: export contacts as a CSV.
   - Or they can email the file to their own Openbook address, which withopenbook.com/find-people gives them, or turn on Syncing in Openbook's iPhone app, which sends every contact as the phone holds it, without this app.
3. **In ChatGPT, pass the file itself** as `contacts_file` of `add_to_private_contacts`, with `done: true`: Openbook reads every card in it, as it reads an emailed one. Skip to step 6.
4. **Anywhere else, read every field of each card** and send it as its `card`, the contact as an iPhone holds it, leaving nothing out:
   - A line that starts with a space or a tab continues the one before it.
   - `N` is family, given, middle, prefix and suffix: `familyName`, `givenName`, `middleName`, `namePrefix`, `nameSuffix`; `NICKNAME`, `X-MAIDENNAME` (`previousFamilyName`), the `X-PHONETIC-` names, `ORG` (company, then department), `TITLE` (`jobTitle`) and `NOTE` (`note`).
   - Lists, each entry `{ label, value }` in the file's order: `TEL` (`phoneNumbers`), `EMAIL`, `ADR` (`postalAddresses`, `{ street, city, state, postalCode, country }`), `URL`, `X-ABDATE` (`dates`, `{ year, month, day }`), `X-ABRELATEDNAMES` (`contactRelations`), `X-SOCIALPROFILE` (`socialProfiles`, `{ urlString, username, service }`) and `IMPP` (`instantMessageAddresses`, `{ username, service }`); `BDAY` is `birthday`, without its year when it's 1604 or left out.
   - A label is its `TYPE`, like CELL or HOME, or a custom one on its own line in the same group, like `item1.X-ABLabel`; send it as written, Apple's own like `_$!<Mobile>!$_` too.
   - A contact with no number goes too; only numbers count toward the people they know.
   - Skip the person's own card, and Openbook's own cards, which carry Openbook's links, like Open in Openbook, Share Details or Request mobile, and their groups in the company, like “Coaches” or “Acme Corp • Coaches”, or read “Openbook”: Openbook shows those already. Send each card's links in it all the same, and Openbook leaves its own out.
5. **Ask who to keep out** before sending, like a doctor or an ex. You can leave them out, or hide them after with `hide_contacts`, so nobody can ask about them through the person.
6. **Send** with `add_to_private_contacts`, up to 500 contacts a call, and `done: true` on the last call.
7. **Report** how many went in, and offer what's next:
   - finding someone now (`find-through-people-you-know`);
   - letting only people in their contacts send them requests (`update_settings` `requests_from: "contacts"`, see `request-controls`);
   - showing Private Contacts on their phones (`update_settings` `groups` with its ID from `my_access` and `shown: "in_contacts"`), which puts those contacts beside their phone's own cards for the same people.
8. **Sending again later** updates each contact: matched by its card, its mobile number or its name, it takes what's new and changed, and nothing anyone edited in Openbook is lost. Each contact's history (`contact_history`) shows what came, and `revert_contact_change` puts a contact back as an earlier send left it. To take them all out, they use Delete the contacts you added on Manage Account.
