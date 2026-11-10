---
name: import-from-email
description: Build an Openbook group from an email group (a Google Group, a groups.io group or any mailing list) or a reply-all thread, reading the person's email with this app's own access: asking where it goes, taking every sender's name and email and the numbers people give about themselves, naming the email group it came from, confirming before adding, then helping people join.
---

# Import from an email group

Use this when the people the person wants in a group are on an email group or a thread: a neighborhood Google Group, a groups.io group, a school's or club's mailing list, a book club's reply-all thread. A subscriber export, a CSV from the email group's own pages, follows `import-a-spreadsheet`, then steps 4 and 10 here.

## 1. Find the email group

- Call `my_access`.
- Read the email with this app's own access, like a Gmail or Outlook connection the person added here. Openbook never reads anyone's email: what you read stays between the person and this app until they say yes to adding someone. Without that access, ask them to paste or forward the messages, or, for an email group they own or moderate, to download its subscribers as a CSV from its own pages.
- Find its address and its name: the address its posts go to, like maple-court@googlegroups.com or maplecourt@groups.io, from the To or List-Id of its messages, and its name, from the brackets that start its subjects, like [maplecourt], or its own pages. In Gmail, list:maple-court@googlegroups.com finds its messages. Confirm both with the person.
- A reply-all thread with no address of its own isn't an email group: go on with the people who wrote to it, with no `email_group` to set, and they can reply to the thread with the group's link at the end.

## 2. Gauge its size

- Count the different people who posted in the time the person picks, like the last year, and say it: “About 140 people posted to Maple Court since last November.”
- Posts only find people who write. For an email group they own or moderate, the subscriber export from its own pages has everyone, people who never post too, and imports as in `import-a-spreadsheet`.

## 3. Ask where it goes

Explain both plainly, suggest one for its size, and let them pick:

- **A directory of its own,** named for the community: `create_organization` with `name` (“Maple Court”), `first_group` for who's in it (“Neighbors”), `rules` and `email_group`. They own it, and everyone who joins sees it under the community's name, “Maple Court • Neighbors” on their phones. They can keep it **Only in search** on their own phones (`update_settings` `groups` with the group's ID and `shown: "only_in_search"`): its contacts turn up when they search in Contacts on an iPhone or iPad, without filling their Contacts with every neighbor. An organization's free plan holds 25 users, so a bigger community needs a plan to let everyone in: say so, with no price, and point to withopenbook.com.
- **A group of their own in Personal,** like Book Club: `create_organization` with no `name`, and `first_group`, `rules` and `email_group`. Others in it see it by its name alone, “Book Club”. It stays Hidden on the person's own phones until they show it (Show in Contacts, `update_settings` `groups` with `shown: "in_contacts"`), and a group in Personal can't be Only in search. Good for a small circle.

A group they already run that came from this email group takes it with `manage_groups` `update`, its `group` and `email_group`.

## 4. Name the email group

- Set `email_group` to the email group's address on the group, confirming the address with the person. Openbook keeps it for the people who manage the group and never shows it to anyone else.
- Say what it can bring, in these words: “If yours is the first group from this email group that 5 people join, your QR Card becomes a Founding Member card.” Never promise it, and never say whether the email group is on Openbook already: Openbook doesn't say, so you can't know (`founding-member`).

## 5. Find the people

- **Every sender's name and email** over the time picked. Page through the search until there are no more results; for a busy email group, go a month at a time.
- **Their own address.** A Google Group can send a post From its own address, like “Maya Lee via Maple Court” <maple-court@googlegroups.com>: the person's own is then in Reply-To, or in their signature. groups.io writes one as maya.lee=example.com@groups.io, which is maya.lee@example.com. Without their own address, leave them out and say so.
- **Leave out** the email group's own addresses (its owners' and moderators' too, like maplecourt+owner@groups.io), no-reply and bounce senders (noreply, no-reply, mailer-daemon, postmaster), digests and the email group's own notices, the person themselves, and anyone who asked to be left off.
- **A thread:** everyone who wrote to it, by the name and address in each message's From. Ask before adding people who were only copied.
- **Names** as people sign, “Maya Lee” rather than maya.lee; ask about an address with no name.
- **One contact per person.** Someone posting from two addresses is one contact with both, but only when you're sure: ask.

## 6. Find the numbers people give about themselves

People often put their number in their signature. Search every message each person sent:

- **Only what they wrote.** Skip quoted text: lines starting with “>”, and everything after a line like “On Mar 3, 2026, at 9:14 AM, Ruth Park wrote:”, “-----Original Message-----” or a forwarded message's header (“Begin forwarded message:”, or its From, Sent, To and Subject lines).
- **Only their own:** in their signature, the lines after their name at the end of what they wrote, or about themselves, like “call me at” or “my cell is”. Never a number they give for someone else, a business or another neighbor.
- **US numbers in every format:** 10 digits with an optional +1 or 1, not part of a longer run of digits.

  ```
  (?<!\d)(?:\+?1[\s.-]?)?\(?([2-9]\d{2})\)?[\s.-]?(\d{3})[\s.-]?(\d{4})(?!\d)
  ```

  It finds (415) 555-0148, 415-555-0148, 415.555.0148, +1 415 555 0148 and 4155550148, and Openbook takes any of them as written.
- **Labeled by the cue next to it:** M, C, Cell or Mobile is `mobile`; O, Office, W, Work or Direct is `work`; H or Home is `home`; skip Fax. Ask about one with no cue: “Ruth Park signs with (415) 555-0148 and no label. Is that her mobile?”
- **The newest wins:** when someone's signature changed numbers, take the one in their latest message.
- **Keep where each came from,** to say when you confirm.

## 7. Set who sees what, before adding

A new group shows only Notes until its rules are set. Suggest, unless the person says otherwise:

- `email` Visible: people on an email group already see the addresses of the people who post.
- `phone.mobile` Request required, and `phone.work` and `phone.home` too: people put a number in a signature for one email, not for a directory.

Set them with the group: `rules` on `create_organization`, or `manage_groups` `update`.

## 8. Confirm

Say the counts, where it goes, the rules, the email group, and where each number came from: “About 140 people posted to Maple Court since last November. I'll create Maple Court with one group, Neighbors, naming maple-court@googlegroups.com as the email group it came from: everyone's name and email, with emails visible, and 23 mobile numbers from people's own signatures, which others request. Maya Lee's (415) 555-0142 is from her signature on March 3. Shall I add them?”

## 9. Import

- `import_contacts` with the group, up to 500 contacts a call; split a bigger email group and keep going until everyone's in. Each contact is `{ name, fields: [{ type: "email", value }, { type: "phone", label: "mobile", value }] }`.
- One number Openbook can't read refuses the whole call, so check them first.
- Report how many were added, how many joined contacts the directory already had and got details they didn't have (`filled`), and anything left out and why.

## 10. Help people join

People joining is what makes the group useful, and what counts for Founding Member. Offer either:

- **Post the group's invite link to the email group, themselves.** The group's `share_page` in `my_access` opens its Share page, with its QR code and their invite link, like withopenbook.com/K7M2PQ9XRA, and Copy link: give it as a link for them to open. The invite link goes in the post, never the Share page's own address, which is theirs. Offer to draft the post for them to send from their own email: what the group is, that it shows up in everyone's phone contacts, what everyone in it sees and what takes a request, and the link. A new group lets people who ask to join from its link in right away, unless it was made otherwise. Openbook sends nothing to the email group.
- **Invite each person by email:** `invite_users` with `people` and `add_to_group: false`, since they're in the group as contacts already (`invite-people`). Openbook emails each invite, up to 500 a day.

Someone who joins from the invite link becomes a contact in the group too, with their name, mobile number and email (`add_from_links`). Only a mobile number matches them to a contact already there, so someone imported with only an email shows twice until you merge the two (`tidy-contacts`).
