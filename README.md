# Advent Calendar | AppADay 192

A Catholic family Advent calendar builder. Add the people in your home with their ages, choose a theme, and Claude writes one door for each day from the First Sunday of Advent to Christmas Eve. Each door holds a short title, a Scripture passage told in paraphrase, and a reflection, an activity and a prayer for every age group in your family.

**Live app:** https://augustineiacopelli.github.io/augustineiacopelli-appaday-192-advent-calendar-builder/
**Portfolio:** https://augustineiacopelli.github.io/appaday/

Category S (Spiritual). Claude powered.

## Every year

The calendar computes itself for whatever year it is opened in. Advent starts on the fourth Sunday before Christmas, so it runs 22 to 28 days and the door count changes with it (26 doors in 2026, starting November 29). From February onward the app shows the coming Advent, and in January it still shows the one just past. It also works out:

* the Lectionary cycle (2025 A, 2026 B, 2027 C) and that year's four Sunday Gospels
* the Gaudete (rose) Sunday
* which saints' days give way to a Sunday of Advent (St. Nicholas, Our Lady of Guadalupe and St. Lucy keep their customs)
* moving the Immaculate Conception to Monday when December 8 falls on a Sunday
* the years when Christmas Eve is also the Fourth Sunday of Advent

The Jesse Tree has 28 ornaments and drops Gideon, Esther, Joshua, Solomon, Jonah and Daniel, in that order, in shorter years. The Works of Mercy plan pairs the works across however many weekdays there are. Doors are stored by date, so a new Advent starts with an empty calendar and keeps the family and theme from the year before. Add `?year=2027` to the URL to preview another year.

## St. Nicholas and the Immaculate Conception

In every theme, St. Nicholas (December 6) and the Immaculate Conception (December 8) are required content for every age group, not just background. Their calendar tiles are marked in rose, and their doors carry a Feast chip. December 5 adds a St. Nicholas Eve note that invites the family to set out shoes. On December 8 the door mentions that it is a Holy Day of Obligation in the United States. When the feast moves to Monday, the door says so and leaves out the obligation, which does not move with it.

## How it works

1. **Family.** Add names and ages. Ages place each person in one of four age groups: Little Ones (0 to 5), Children (6 to 11), Teens (12 to 17) and Adults (18 and up). Only the age groups present in your home are written. Names never leave the device and appear only on printed pages.
2. **Theme.** Pick one of five, or describe your own:
   * **Jesse Tree** keeps a fixed passage and ornament symbol each day, from Creation to the manger.
   * **Liturgical Year** follows the Sunday Gospels for the year's Lectionary cycle, the feasts of Advent, and the prophecies behind the O Antiphons on December 17 to 23.
   * **Works of Mercy** gives each weekday one or two of the fourteen corporal and spiritual works, with Sundays as review days and Christmas Eve gathering all fourteen.
   * **With Mary** keeps fixed Gospels on Marian days (Immaculate Conception, Loreto, Guadalupe, and the late Advent Gospels) and views every other day through Mary's waiting.
   * **Advent Saints** honors the saint on the calendar, or a biblical figure of Advent on days without one.
   * **Custom** layers your own description over the Sunday Gospels and O Antiphons.
3. **Generate All** writes the doors one at a time and saves each as it arrives. You can stop it and resume later, and a door that is cut short is retried in smaller pieces.
4. **Open a door** on its day. Doors before today stay locked unless Preview mode is on in Settings. Each door has a tab for each age group, and you can edit the reflection, activity or prayer with the Edit button and its inline Save. Regenerating a door you edited asks first.
5. **Print** one door, or every door for one age group or for all of them. Each age group gets its own page in black on white with a gold rule, and each page names the family members in that age group.

## Settings (gear)

Claude API key (shared AppADay key ring), family editing, theme change (clears written doors after confirmation), Preview mode, Print All with an age group selector, backup download and restore, and Reset.

## Privacy

Everything is stored in this browser under `appaday-192-state`. A request to Claude carries the date, the day's liturgical label, the theme anchor, any fixed Scripture reference, the theme in a delimited data block, and the list of age groups. Family names and ages are never sent. A custom theme is cleaned of control characters and markup and capped at 160 characters before it is sent.

## Technical notes

Single self-contained `index.html` with HTML, CSS and vanilla JavaScript, and Cormorant Garamond and Inter from Google Fonts. The model comes from the portal's shared `models.js` (sonnet tier), and the API key comes from the shared `keys.js` key ring. Requests use `max_tokens` 1800 and step through the accepted forms of the `thinking` field, remembering which form worked for each model. Only text blocks are read from the reply. Replies are strict JSON, and any fixed Scripture reference is enforced on the client as well as in the prompt. The app avoids `window.confirm` and uses its own confirm dialog.

Scripture references follow NABRE verse numbering. Claude paraphrases each passage and does not quote any translation.

Part of [AppADay](https://augustineiacopelli.github.io/appaday/), one complete web app shipped every day.
