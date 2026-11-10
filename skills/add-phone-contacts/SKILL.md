---
name: add-phone-contacts
description: Bring the person's own phone contacts into Openbook with Find people through contacts: from an iPhone's exported All Contacts file, a Google Contacts, Mac or Outlook export, or numbers they paste, so people they know can ask them for someone, and they can find people through people they know.
---

# Add the contacts on their phone

Find people through contacts is how someone's own contacts come into Openbook. It's what lets them find people through people they know (`find-through-people-you-know`), and lets people they know ask them for a contact. It takes only names, numbers and emails. To keep their contacts in Openbook with every detail, as their address book or to share with someone, follow `host-your-contacts` instead.

1. **Explain first, in these terms:** nobody sees their contacts; people they know can ask them for one when they're looking for someone; nothing is shared unless they say yes. Their contacts go into My Contacts, a group in Personal that stays off their phones until they show it. What they send passes through this app's provider on its way to Openbook.
2. **Get the file.**
   - iPhone: in Contacts, tap Lists at the top, hold All Contacts, choose Export, tap the check mark, then pick this app and send the file here.
   - Mac: in Contacts, select All Contacts, then File, Export, Export vCard.
   - Android or Google Contacts on the web: Export, as a vCard or a Google CSV.
   - Outlook: export contacts as a CSV.
   - Or they can email the file to their own Openbook address, which withopenbook.com/find-people gives them, without this app.
3. **Read it.** For each contact, take only the name, phone numbers and emails, and drop every other line as you go.
   - A line that starts with a space or a tab continues the one before it.
   - Name: `FN`, or else `N`'s parts as “given middle family”.
   - Phones (`TEL`): CELL, MOBILE and IPHONE are `mobile`, HOME `home`, WORK and MAIN `work`; skip FAX and PAGER. A custom label is its own line in the same group, like `item1.X-ABLabel`, and Apple's own read like `_$!<Mobile>!$_`: take what's between `<` and `>`, in lowercase.
   - Every contact needs a phone number, so skip those without one, and merge cards with the same number.
   - Skip the person's own card, and Openbook's own cards, whose names end with a group, like “Hana Sato • Coaches”, or read “Openbook”: Openbook shows those already.
4. **Send nothing else.** Notes, addresses, birthdays, photos and the file itself are refused: build each contact as `{ name, fields: [{ type: "phone", label, value }, { type: "email", value }] }`.
5. **Ask who to keep out** before sending, like a doctor or an ex. You can leave them out, or hide them after with `hide_contacts`, so nobody can ask about them through the person.
6. **Send** with `add_to_my_contacts`, up to 500 contacts a call, and `done: true` on the last call.
7. **Report** how many went in, and offer what's next:
   - finding someone now (`find-through-people-you-know`);
   - letting only people in their contacts send them requests (`update_settings` `requests_from: "contacts"`, see `request-controls`);
   - showing My Contacts on their phones (`update_settings` `groups` with My Contacts' ID from `my_access` and `shown: "in_contacts"`), which puts those contacts beside their phone's own cards for the same people.
8. **Sending again later** adds what's new: contacts already in My Contacts are matched by mobile number, and nothing is deleted. To take them all out, they use Delete the contacts you added on Manage Account.
