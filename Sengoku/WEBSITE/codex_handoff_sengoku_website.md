# Codex Handoff - Sengoku Website / Mailing List

Date: 2026-05-29

Project:

Sengoku - Clash of the Daimyo

Main website:

https://sengoku-game.carrd.co/

Workspace folder:

E:\Projects\Intensive\Sengoku\WEBSITE

---

## Current Goal

Prepare the Sengoku website and mailing list for UKGE 2026 playtesting and future pre-crowdfunding audience building.

The website should:

- attract players and potential backers;
- explain the game quickly;
- collect mailing list subscribers;
- provide rulebook access;
- provide publisher/manufacturer information;
- offer a contact route;
- support QR codes printed on cards and event material.

---

## Website Structure

The current Carrd site has these main sections:

1. Initial Sengoku / historical-theme section
2. The Game
3. Why it feels different
4. On the table
5. Every turn can shift the balance
6. Subscribe / mailing list
7. How to Play / Rulebook
8. Publisher Info / Sell Sheet
9. Contact
10. Footer

Recommended footer text:

```text
[Join List](#subscribe) | [How to Play](#how-to-play) | [Publisher Info](#publisher-info) | [Contact](#contact)
```

Colored-link attempt for Carrd:

```text
[[Join List]{#c9a24a}](#subscribe) | [[How to Play]{#c9a24a}](#how-to-play) | [[Publisher Info]{#c9a24a}](#publisher-info) | [[Contact]{#c9a24a}](#contact)
```

Known marker IDs:

```text
#subscribe
#how-to-play
#publisher-info
#contact
```

Possible future marker:

```text
#videos
```

---

## Main Copy Decisions

Game title:

```text
Sengoku - Clash of the Daimyo
```

Avoid writing:

```text
Set during Japan's Sengoku period, Sengoku...
```

because repeating Sengoku sounds awkward.

Preferred wording:

```text
Clash of the Daimyo
```

or:

```text
the game
```

---

## Hero Copy

Use `path` rather than `road` here, because `road` is used for mailing-list/campaign language.

```text
A strategic board game of clans, alliances,
and ruthless ambition in feudal Japan.

Lead your daimyo,
exploit your rivals' mistakes,
and fight for influence
on your path to Shogun.
```

---

## Sengoku Jidai Section

Carrd Markdown:

```text
[Sengoku Jidai]{#c9a24a}
*the Warring States period of Japan*

**A brutal age. A strategic game.**

[Clash of the Daimyo]{#c9a24a}
turns Japan's Warring States period
into a tense strategy game of shifting alliances,
ambition, betrayal, and war.

[Do not attack blindly.]{#c9a24a}
Read the board.
Time your moves.
Punish exposed mistakes.
```

---

## The Game Section

Heading:

```text
The Game
```

Body:

```text
[Sengoku - Clash of the Daimyo]{#c9a24a}
is a medium-weight strategy board game
for 2-4 players,
with an expanded version planned for up to 6.

Lead rival daimyos, build influence,
and forge unstable alliances.

Use asymmetric decks
to claim the title of Shogun.
```

Quote:

```text
Easy to learn.
Hard to read.
Cruel when you stop paying attention.
```

There is a red How to Play button in this section.

---

## Why It Feels Different

Heading:

```text
Why it feels different
```

Body:

```text
[Conquest is not always the answer.]{#c9a24a}

Influence, timing, and alliances
can be stronger than direct attack.

[No player is ever completely safe.]{#c9a24a}

Mistakes can be spotted,
punished,
and turned against you.

[No waiting around.]{#c9a24a}

Every move can open a chance,
create a threat,
or change the balance of power.
```

---

## On The Table

Heading:

```text
On the table
```

Body:

```text
A physical prototype is already on the table,
tested and refined through repeated play sessions.
```

Captions:

```text
Number cards, retainers, and daimyo cards.

Player board, discard deck, and gained Koku.

Protection tokens, castles, and the Shogun token.
```

---

## Every Turn Can Shift The Balance

Quote above:

```text
"Lead territories, command armies,
and forge alliances
to gain influence, resources, and prosperity.

The path to Shogun
shall be your triumph."
```

Heading:

```text
Every turn can shift the balance
```

Body:

```text
Build your chain of command,
protect key positions,
and reveal hidden cards at the right moment.

[Rebellions]{#c9a24a} can break control.
[Traps]{#c9a24a} can punish careless moves.
[Alliances]{#c9a24a} can protect you,
or become a dangerous dependency.

Even the [Emperor]{#c9a24a}
can change the rhythm of the game.
```

Quote below:

```text
"My favourite part? Catching mistakes.
Solving errors is brilliant."
```

---

## Subscribe / Mailing List

The naming was adjusted from "pre-launch list" to broader "Sengoku updates" language, because the list should allow:

- development updates;
- playtest news;
- event announcements;
- historical notes;
- design insights;
- crowdfunding news.

Recommended title:

```text
Subscribe to Sengoku updates
```

Body:

```text
Join the pre-launch list and follow the road to Shogun:
development updates, playtest news, event announcements,
historical notes, design insights, and crowdfunding news.
```

Button:

```text
Join the List
```

Microcopy:

```text
No spam.
Only meaningful updates about
Sengoku - Clash of the Daimyo.
```

MailerLite group:

```text
Sengoku Mailing List
```

MailerLite Group ID seen in URL:

```text
188627004409513673
```

Do not expose MailerLite API token in chat or files.

Double opt-in for API/integrations was enabled in MailerLite.

Important MailerLite behavior:

- Confirmation email may only send once per subscriber every 24 hours.
- Use Gmail `+alias` addresses for tests, e.g. `intensive.games.design+test1@gmail.com`.

---

## Welcome Email

The welcome email should be handled by MailerLite Automation, not by the confirmation email.

Recommended trigger:

```text
When subscriber joins group: Sengoku Mailing List
```

Important:

There were two automations. The correct one should be active:

```text
Simple welcome email
```

The other workflow based on "subscriber completes a form" was less reliable for Carrd/API.

Welcome email text:

```text
Thank you for joining the Sengoku - Clash of the Daimyo mailing list.

Your place on the road to Shogun is now secured.

From here, I'll share new content as the game moves toward crowdfunding:
playtest news, artwork, development updates, and availability.

You'll be among the first to know when the next banner is raised.

It is an honor to have you with us.

Gianluca
Intensive Games
```

---

## How To Play

The How to Play section should follow the local V26 rulebook:

```text
E:\Projects\Intensive\Sengoku\RULEBOOK\V26\Sengoku V26.docx
```

V26 facts:

- 2-4 players
- 45-90 minutes
- 12+
- Chain starts from Daimyo
- Control zones and disputed spaces
- Koku income
- Prefecture cards and Retainers
- Rebellions
- Protection, Markets, Castles, Capital
- Imperial Summons final round

Short How to Play text:

```text
Lead your Daimyo clan
and expand your chain of command.

Place cards,
control key areas,
gain Koku,
and build your path to Shogun.
```

Steps:

```text
[Build your chain]{#c9a24a}
Only cards connected to your Daimyo
can score.

[Control the board]{#c9a24a}
Use Prefecture cards
to claim zones and disputed spaces.

[Use Retainers]{#c9a24a}
Play allies, attacks,
traps, and tactical effects.

[Watch for Rebellions]{#c9a24a}
Matching numbers in the same zone
can break control.

[Build your Capital]{#c9a24a}
Use Koku and Protection
to build Markets, Castles,
and finally your Capital.

[Face the Imperial Summons]{#c9a24a}
After a Capital is built,
one final round decides the winner.
```

Rulebook disclaimer:

```text
Disclaimer: The current rulebook is still in development.

The rules are the most up-to-date version,
but layout, images, and presentation are not final
and do not represent the final quality of the product.
```

Short phrase for each rulebook page:

```text
Development preview - rules are current, presentation is not final.
```

A4 printable rulebook link text:

```text
Prefer a cleaner version?
[View the A4 print-friendly rulebook](PDF_LINK_HERE).
```

---

## Publisher Info

Heading:

```text
Publisher Info
```

Intro:

```text
Sengoku - Clash of the Daimyo is a medium-weight strategy game for players who enjoy tactical depth, strong interaction, and historical themes.

The game is currently in prototype refinement, with updated rules, playtest feedback, and production planning in progress.
```

Key facts:

```text
[Players]{#c9a24a} 2-4 players

[Play time]{#c9a24a} 45-90 minutes

[Age]{#c9a24a} 12+

[Status]{#c9a24a} Playable prototype in active refinement

[Core experience]{#c9a24a} Card placement, territorial control, asymmetric retainers, rebellions, traps, and a race to build the Capital.
```

Development note:

```text
The current version is designed as a base game for 2-4 players. Future development may include an expanded version or special edition with additional player count, upgraded components, and refined production materials.
```

Buttons:

```text
Download Sell Sheet
Contact Intensive Games
```

---

## Contact Form

Recommendation:

Do not send contact form messages into MailerLite for now.

Keep separate:

```text
Subscribe form -> MailerLite
Contact form -> intensive.games.design@gmail.com
```

Contact section:

```text
Contact Intensive Games
```

Text:

```text
For publisher enquiries, manufacturing discussions, playtest feedback, or collaboration, get in touch.
```

Form type:

```text
Contact
```

Fields:

```text
Name
Email
Message
```

Recipient:

```text
intensive.games.design@gmail.com
```

Spam protection:

Cloudflare Turnstile if easy; otherwise Default is acceptable.

Completion message:

```text
Thank you. I'll get back to you soon.
```

Privacy footer text:

```text
Your interest matters, and so does your privacy.
We'll only use your details to reply to you or send the updates you asked for.
```

---

## UKGE 2026 Event Banner

Event details:

- UKGE 2026, Birmingham
- Playtest Zone
- Hall 2 - Stand 108 (2-108)
- Saturday 30 May 2026
- 1:30pm - 4:30pm
- Expo entry ticket required
- Latest Sengoku prototype available to play
- Small sweets/candies available
- Visitors can talk directly with Gianluca
- Visitors can give feedback and sign up for future online playtest sessions

Wide Carrd text:

```text
[May 2026]{#59C242}

Play the latest version of [Sengoku - Clash of the Daimyo]{#c9a24a} at [UKGE 2026]{#c9a24a}.

Sit at the table, test the newest prototype, grab a small sweet, and share your feedback directly with the designer.

You can also join the mailing list and sign up for future online playtest sessions.

**Saturday 30 May | 1:30pm - 4:30pm**
**Playtest Zone - Hall 2, Stand 108 (2-108)**

Expo entry ticket required.
```

Do not publish Playtest UK private mobile/email details unless explicitly intended.

---

## QR Code

Generated QR files:

```text
E:\Projects\Intensive\Sengoku\WEBSITE\sengoku-ukge-2026-subscribe-qr.png
E:\Projects\Intensive\Sengoku\WEBSITE\sengoku-ukge-2026-subscribe-qr.svg
```

Generated URL:

```text
https://sengoku-game.carrd.co/?utm_source=ukge&utm_medium=qr&utm_campaign=ukge_2026#subscribe
```

For small printed labels, a shorter URL is more reliable:

```text
https://sengoku-game.carrd.co/#subscribe
```

QR printing notes:

- Minimum practical QR size: 25 x 25 mm.
- Safer size: 28-30 mm.
- Use black QR on white background.
- Leave quiet zone / white border around QR.
- Recommended quiet zone: at least 4 modules, practically 3-5 mm.
- Avoid logo in the QR for small labels.
- If using a logo, QR should be larger, around 35 mm, and error correction high.

Label copy options:

```text
The path to Shogun awaits

[QR]

Scan to discover
Sengoku - Clash of the Daimyo.
```

Or:

```text
Enter the world of Sengoku

[QR]

Discover the game
and walk the path to Shogun.
```

Recommended card-label size:

```text
35 x 45 mm
```

Recommended QR size inside label:

```text
25-28 mm
```

---

## Files Created During This Work

Reference backups:

```text
E:\Projects\Intensive\Sengoku\WEBSITE\index_page_2025.md
E:\Projects\Intensive\Sengoku\WEBSITE\index_page_2026.md
```

QR:

```text
E:\Projects\Intensive\Sengoku\WEBSITE\sengoku-ukge-2026-subscribe-qr.png
E:\Projects\Intensive\Sengoku\WEBSITE\sengoku-ukge-2026-subscribe-qr.svg
```

Handoff:

```text
E:\Projects\Intensive\Sengoku\WEBSITE\codex_handoff_sengoku_website.md
```

---

## Next Suggested Work

1. Verify all Carrd links after publish:
   - #subscribe
   - #how-to-play
   - #publisher-info
   - #contact
2. Test QR on printed paper/card before cutting many labels.
3. Test subscription with a fresh Gmail +alias.
4. Test contact form delivery.
5. Prepare QR label A4 sheet if needed.
6. Add Videos section later:
   - #videos
   - keep one video on landing;
   - collect additional videos in Videos section.
7. Later differentiate MailerLite groups for additional games:
   - Sengoku Mailing List
   - The King's Favour Mailing List
   - separate welcome automations per group.

