---
name: import-from-email
description: Build an Openbook group from an email group (a Google Group, a groups.io group or any mailing list) or a reply-all thread in as few turns as possible: one pass reading the person's email with this app's own access, one message with every question and a suggestion for each, then the whole job without stopping, its subscribers or every sender's name and email, the numbers people give about themselves, duplicates merged, the email group named and people helped to join, with a checkpoint if the turn ends first.
---

# Import from an email group

Use this when the people the person wants in a group are on an email group or a thread: a neighborhood Google Group, a groups.io group, a school's or club's mailing list, a book club's reply-all thread.

**The person's turns are the cost.** Each answer they give, and each “keep going”, is a turn. The whole job takes three: you ask everything at once, they answer, you finish and report. Never stop to show progress, to ask whether to go on, or to ask a question you could have asked in the one message.

Read the email with this app's own access, like a Gmail or Outlook connection the person added here. Openbook never reads anyone's email: what you read stays between the person and this app until they say yes to adding someone. Without that access, ask them to paste or forward the messages, or to attach a subscriber export.

## 1. Gather everything first, in one pass

Do all of this before saying anything, in as few calls as you can.

- **Their directories and groups:** `my_access`.
- **The email group:** its address, like maple-court@googlegroups.com or maplecourt@groups.io, from the To or List-Id of its messages, and its name, from the brackets that start its subjects, like [maplecourt]. In Gmail, list:maple-court@googlegroups.com finds its messages. A reply-all thread with no address of its own isn't an email group: go on with the people who wrote to it, with no `email_group` to set.
- **The roster, from senders alone.** Ask the mail search for the largest page it gives and read only each message's From and Reply-To, never its body: that's every sender's name and email in a few calls, where reading each message takes hundreds. Page through to the end of the time the person asked about, or the whole archive.
  - **Their own address.** A Google Group can send a post From its own address, like “Maya Lee via Maple Court” <maple-court@googlegroups.com>: the person's own is then in Reply-To. groups.io writes one as maya.lee=example.com@groups.io, which is maya.lee@example.com. Without their own address, leave them out.
  - **Leave out** the email group's own addresses (its owners' and moderators' too, like maplecourt+owner@groups.io), no-reply and bounce senders (noreply, no-reply, mailer-daemon, postmaster), digests and the email group's own notices, the person themselves, and anyone who asked to be left off.
  - **Names** as people sign, “Maya Lee” rather than maya.lee. One person posting from two addresses is one contact with both.
- **Numbers, from bodies, in one pass.** Search for messages likely to carry one (cell, mobile, phone, call, text, or digits), then read only those bodies, each once:
  - **Only what they wrote.** Skip quoted text: lines starting with “>”, and everything after a line like “On Mar 3, 2026, at 9:14 AM, Ruth Park wrote:”, “-----Original Message-----” or a forwarded message's header (“Begin forwarded message:”, or its From, Sent, To and Subject lines).
  - **Only their own:** in their signature, the lines after their name at the end of what they wrote, or about themselves, like “call me at” or “my cell is”. Never a number they give for someone else, a business or another neighbor.
  - **US numbers in every format:** 10 digits with an optional +1 or 1, not part of a longer run of digits.

    ```
    (?<!\d)(?:\+?1[\s.-]?)?\(?([2-9]\d{2})\)?[\s.-]?(\d{3})[\s.-]?(\d{4})(?!\d)
    ```

  - **Labeled by the cue next to it:** M, C, Cell or Mobile is `mobile`; O, Office, W, Work or Direct is `work`; H or Home is `home`; skip Fax. A number with no cue is a question for step 2.
  - **The newest wins** when someone's signature changed numbers.
  - Keep where each came from, to say in step 2, never as its label or in a note.
- **Who's there already:** `search_contacts` in the directory it's going to, with `limit` 500, for the names and emails that match, so step 2 can say who's new and who may be someone already there.
- **Recommendations,** if the person wants them too: find them in the same pass (`import-recommendations`, steps 2 to 8).

## 2. Ask everything in one message

One message, every decision, each with your suggestion, so the person can answer “yes” or change one line. Use the app's choices or a form when it has them. Cover:

- **Where it goes.** Suggest one and say why:
  - **A directory of its own,** named for the community: `create_organization` with `name` (“Maple Court”), `first_group` for who's in it (“Neighbors”), `rules` and `email_group`. Everyone who joins sees it under the community's name, “Maple Court • Neighbors” on their phones, and the person can keep it **Only in search** on their own phones (`update_settings` `groups` with `shown: "only_in_search"`). An organization's free plan holds 25 users, so a bigger community needs a plan to let everyone in: say so, with no price, and point to withopenbook.com.
  - **A group of their own in Personal,** like Book Club: `create_organization` with no `name`, and `first_group`, `rules` and `email_group`. Good for a small circle. It shows on their own phones from the start.
  - A group they already run takes `email_group` with `manage_groups` `update`.
- **The email group's address** for `email_group`, and what it can bring, in these words: “If yours is the first group from this email group that 5 people join, your QR Card becomes a Founding Member card.” Never promise it, and never say whether the email group is on Openbook already.
- **Who sees what:** suggest `email` Visible, since people on an email group see the addresses of the people who post, and `phone.mobile`, `phone.work` and `phone.home` Request required, since people put a number in a signature for one email, not for a directory.
- **Who's in:** the count, like “About 140 people posted to Maple Court since last November”, and a subscriber export instead if they own or moderate the email group, which has everyone, people who never post too (step 3).
- **Names in doubt,** as one list with a rule to apply: “Keep these 6 under the name they post as, like Cindy CU, or leave them out?”
- **Numbers with no cue,** as one list: “These 4 numbers have no label in the signature. Add them as mobile?”
- **Likely duplicates** of contacts already there, by the same email or name, as one list: “Dennis Bartlett is in Personal already by email. Add him to Maple Court as the same contact?”
- **Recommendations** you found, if any, and the group they'd go in.
- **Helping people join** after: post the group's invite link to the email group themselves, or have Openbook email each person an invite (step 5).

End with one line they can say yes to: “Say yes and I'll do all of it, or tell me what to change.”

## 3. Then do the whole job, without stopping

On their answer, do everything in the same turn, with the fewest calls:

1. **Make the group** with its rules and `email_group`, or update the one they picked.
2. **Add everyone at once.** A subscriber export they attached goes in whole as `contacts_file` on `import_contacts`, in one call. Otherwise `import_contacts` with up to 500 contacts a call, each `{ name, fields: [{ type: "email", value }, { type: "phone", label: "mobile", value }], note }`, the note everything people in the group should know about them, read by everyone the Notes rule shows notes to, never how they were found. One number Openbook can't read refuses the whole call, so check them first.
3. **Merge what they said is one person.** `import_contacts` answers with `possible_duplicates`: merge every pair they agreed to in one `merge_contacts` call, `pairs: [{ keep, other }]`, keeping the contact that was there first. Pairs they weren't asked about wait for the report.
4. **More notes and fields later, many contacts at once:** `add_note` with `notes: [{ contact, text }]` and `update_contact` with `edits: [{ contact, changes }]`, up to 500 each call. Notes follow `openbook`'s rules: plain facts, nothing about how a contact was found, no source, no hedging.
5. **Recommendations,** if they said yes (`import-recommendations`, steps 9 and 11).

## 4. If the turn ends first, leave a checkpoint

The app can end a turn after so many calls. If it does before the job is done, end with:

- what's done, in counts, like “Added 74 of 140 to Maple Court • Neighbors, with 8 mobile numbers”;
- exactly where to pick up, like “Next: senders from before June 2025, then merging 3 pairs”;
- one line to send: “Say continue and I'll pick up there.”

On “continue”, start from that checkpoint. Never read again what was read, or ask again what was answered.

## 5. Report, and help people join

Say how many were added, how many joined contacts already there and got details they didn't have (`filled`), how many were merged, what was left out and why, and any likely duplicates nobody was asked about, with a yes to merge them. Then, as they picked in step 2:

- **The invite link, posted by them.** The group's `share_page` in `my_access` opens its Share page, with its QR code and their invite link, like withopenbook.com/K7M2PQ9XRA, and Copy link. The invite link goes in the post, never the Share page's own address. Offer a draft for them to send from their own email: what the group is, that it shows up in everyone's phone contacts, what everyone in it sees and what takes a request, and the link. Openbook sends nothing to the email group.
- **An email to each person:** `invite_users` with `people` and `add_to_group: false`, since they're in the group as contacts already (`invite-people`). Openbook emails up to 500 invites a day.

Someone who joins from the link becomes a contact in the group with their mobile number, and only a mobile number matches them to a contact already there, so someone imported with only an email shows twice until merged: `search_contacts` with `duplicates: true` finds them, and `merge_contacts` merges them (`tidy-contacts`).
