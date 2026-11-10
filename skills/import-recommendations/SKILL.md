---
name: import-recommendations
description: Turn an email group's recommendations into an Openbook group of the businesses and people a community recommends: finding the hashtags its posts use, like #recommendation or #ISO, and the person's own keywords, in messages they sent and received, each contact with a shared note saying who recommended them, when and why, confirmed before adding.
---

# Import recommendations

Use this when the person wants the plumbers, tutors, sitters and doctors their community recommends kept in one group, like Maple Court • Recommended.

1. **Where.** Call `my_access`. Suggest a group named for it, like Recommended, in the community's directory or in Personal, and make it if needed (`manage_groups` `create` with the `directory`, or `create_organization`). A Recommended group isn't the one made from the email group, so leave `email_group` off it: set that only on a group that really is the email group's own (`import-from-email`).
2. **Find the messages** with this app's own access to the person's email, or what they paste or forward: the email group's posts (in Gmail, like list:maplecourt@groups.io), and the messages the person sent and received about them, replies sent to them directly too.
3. **Find its hashtags first.** Many email groups put hashtags in a post's subject, like “[maplecourt] #recommendation Plumber for an old house?”. Scan the subject line of every message for words starting with #, count each however it's capitalized, and show the most used with their counts: “#recommendation 212, #ISO 96, #forsale 80, #lostandfound 41, #event 33. Which should I collect?”
   - Recommendations: #recommendation, #recommendations, #rec, #recs, #reco, #recommend and #referral.
   - Requests, whose replies carry the recommendations: #ISO (“in search of”), #lookingfor, #ask, #question, #help and #wanted. Read the whole thread.
   - Ask for words of their own to look for too, like “can anyone recommend” or “does anyone know a good”. An email group without hashtags takes those words alone, in subjects and posts.
4. **For each recommendation, take:** who's recommended (a business or a person), what for (plumber, math tutor), their phone, email, website (`url`) and address as the post gives them, who recommended them, when, and a short line of why in the recommender's own words. Read only what the recommender wrote, never text they quoted (lines starting with “>”, and everything after “On … wrote:”).
5. **Keep it to recommendations.** Leave out requests nobody answered, and #ask, #question or #help posts that don't name anyone to call. Tell the person about any warnings or complaints you find, and let them decide: notes are read by everyone the group's Notes rule shows them to.
6. **One contact per business or person.** Merge repeat recommendations into one contact, with a note for each.
7. **Numbers:** a business's number is `work`. Use `mobile` only for a person's own cell, since mobile numbers identify people.
8. **Who sees what:** these numbers are meant to be called, so suggest Visible for phone, email and website, with Notes Visible. Set the rules before adding.
9. **Confirm:** “I found 37 recommendations under #recommendation and in replies to #ISO since January, like Rivera Plumbing, (415) 555-0161, which Maya Lee said fixed her water heater the same day. Add them to Maple Court • Recommended, each with its note?”
10. **Add, then write the notes.** `import_contacts` (up to 500 a call, as an owner) or `add_contact`; then `add_note` for each recommendation, like “Recommended by Maya Lee, March 2026: fixed our water heater the same day.” The `note` on an add is one only the person adding sees, so the shared notes go in with `add_note`.
11. **Report** how many contacts and notes went in, and that people in the group can now search them, for example “who fixes water heaters?” (`search-contacts`).
