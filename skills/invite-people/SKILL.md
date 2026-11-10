---
name: invite-people
description: Invite people to an Openbook group by email, or with texts the person sends from their own phone, adding them to the group as contacts while inviting them; approve people waiting to join; and explain how invited people get the group on their phones.
---

# Invite people

Openbook is invite only for now, so an invite, a group's code or someone's invite link is how new people get in.

1. **Check who can invite.** Owners and people with Give access on the group can, and so can everyone with access when the group lets them (`anyone_can_invite`). `my_access` says.
2. **Who and how.** Give each person's name in `people`, with a mobile number or an email: `invite_users` emails the invite when there's an email, and otherwise returns an `sms:` link for their number. Give those links to the person to tap and send from their own phone, one per person: Openbook never texts anyone. Up to 500 emailed invites a day each; past that an invite comes back with its link for the person to send.
3. **Access:** what each invited person can do in the group, `view` alone unless the person says more (`add`, `edit`, `delete`). Never more than the person inviting has.
4. **Adding them as contacts:** `add_to_group` is on unless set to false, and adds each named person to the group as a contact with their number and email, which everyone with access to the group then sees by its field rules, before they join. Say so when you confirm. Set it to false for people already in the group, like contacts just imported.
5. **Confirm** the names, how each invite goes, the access and whether they're added as contacts, then call `invite_users`. Each invite in the result says whether its person was added, or why not.
6. **Approvals.** Unless the group approves people automatically (`auto_approve`), invites from people without Give access, and people asking to join from an invite link or the group's QR code, wait. `review_invites` `list` shows them, and `approve` (with the access, never past your own) or `decline` answers each. Say when approving also adds someone to the group as a contact (`adds_to_group`).
7. **What invited people do:** open the invite, sign in with their mobile number and the code texted to it, and choose how the group shows on their phones; on an iPhone, Add to iPhone downloads the profile that puts the group in Contacts.
8. **In person or by a link:** `my_access` gives each group the person can invite to its `share_page`, the group's Share page with its QR code to scan and their invite link to send. Give it as a link to open. The same code is on the group's cards on iPhones.
