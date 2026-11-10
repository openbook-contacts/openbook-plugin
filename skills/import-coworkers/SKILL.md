---
name: import-coworkers
description: Build an Openbook group of the people the person works with, from their email at one company domain like @acme.com, never a free email domain: names and addresses from From, To and Cc, and job titles, companies and numbers from the signatures in messages each person sent, into a group of their own or the company's directory, confirmed before adding.
---

# Import coworkers

Use this when the person wants the people they work with in Openbook: everyone at their company's email domain. For an email group or a thread, follow `import-from-email` instead.

1. **The domain.** Ask for it, from their own work address, like @acme.com, and confirm it. Refuse a free email domain, like gmail.com, googlemail.com, yahoo.com, outlook.com, hotmail.com, live.com, msn.com, icloud.com, me.com, aol.com, proton.me or protonmail.com, and an internet provider's, like comcast.net: those are everyone's, not one company's. Say so, and offer `import-from-email` for a group or thread instead. A subdomain, like @eu.acme.com, counts only when the person says it's the same company.
2. **Read the email** with this app's own access, like a Gmail or Outlook connection the person added here. Openbook never reads anyone's email: what you read stays between the person and this app until they say yes to adding someone. Search for the domain in From, To and Cc, like from:acme.com, to:acme.com and cc:acme.com in Gmail, over the time the person picks, paging until there are no more results.
3. **Find the people.** Each address at the domain, with the name the person signs with. Leave out the person themselves, and addresses that aren't one person, like no-reply@, notifications@, support@, info@, team@, hr@ or a shared calendar's; ask about any you're unsure of. Leave out anyone the person says to.
4. **Read signatures, only in messages each person sent themselves:** their job title, company, work and mobile numbers, and their team or office where it's there. The rules in `import-from-email` hold:
   - only what they wrote, never quoted text (lines starting with “>”, everything after “On … wrote:”) or a forwarded message;
   - only their own numbers, never one they give for someone else;
   - US numbers in every format, 10 digits with an optional +1;
   - labeled by the cue next to each: M, C, Cell or Mobile is `mobile`; O, Office, W, Work or Direct is `work`; H or Home is `home`; skip Fax; ask about one with no cue;
   - the newest wins when someone's signature changed, and keep where each came from.
5. **Ask where it goes,** offering both:
   - **A group of their own in Personal,** like Acme Coworkers: `create_organization` with no `name`, and `first_group` and `rules`. It's theirs: it stays Hidden on their phones until they show it (Show in Contacts), and they can share it with someone they work closely with (`host-your-contacts`).
   - **The company's directory,** if they're the one setting it up for the company: `create_organization` with the company's `name`, a `first_group`, and groups by team or office from the signatures, like Sales and Engineering, or Boston and Austin (`manage_groups` `create`). Offer it; never assume it. An organization's free plan holds 25 users, so a bigger company needs a plan: say so, with no price, and point to withopenbook.com.

   Never set `email_group` here: a company's domain isn't an email group.
6. **Explain requests from others** before importing into Personal: nobody sees their contacts; people they know can ask them for one of these, and nothing is shared without their yes. `hide_contacts` keeps one out.
7. **Set who sees what, before adding.** Suggest `email`, `phone.work`, `title` and `company` Visible, and `phone.mobile` Request required: work details are for work, and a mobile in a signature wasn't given for a directory. A new group shows only Notes until its rules are set.
8. **Confirm** with the counts, where it goes, the rules and where numbers came from: “I found 64 people at acme.com in your email since January: 58 with a job title, 41 with a work number and 12 with a mobile in their own signature, like Dana Ortiz, Product Manager, mobile (415) 555-0174, from her signature on May 12. I'll make Personal • Acme Coworkers with work details visible and mobiles by request. Shall I add them?”
9. **Import** with `import_contacts`, up to 500 a call, each contact with its `title` and `company` fields beside its emails and phones. One number Openbook can't read refuses the whole call, so check them first.
10. **Next:** for the company's directory, offer to invite them (`invite-people`, `invite_users` with `add_to_group: false`, since they're in it as contacts already). For a group of their own, offer to show it on their phones (`update_settings` `groups` with its ID and `shown: "in_contacts"`) or to share it.
