# Opole 1942 Death Register — Księga Zgonów

A searchable transcription of the **1942 death register of the Jewish community of
Opole (Opole Lubelskie), Poland**, held by the Archiwum Państwowe w Lublinie
(State Archive in Lublin), fond 1763, series 1.3, signature **35/1763/0/1.3/28**.

**Live site:** https://mosheberman.github.io/opole-1942-death-register/

Most of the people in this book were Jews deported from Vienna to Opole in 1941
who died there in 1942, before the ghetto's liquidation. Among them is Josef
Bermann (né Lehrhaupt), act Nr. 89.

## What each entry contains

- Name (and the name as spelled in the register's own typed index)
- Age, recorded birthplace, occupation, marital status — as recorded
- Recorded date and time of death, and the recorded cause of death
- The two witnesses (declarants) named in the act
- The Hebrew date of death and the **yahrtzeit** (Hebrew month and day)
- A full Polish transcription of the act
- What **DÖW** (Documentation Centre of Austrian Resistance), **Yad Vashem**
  (Central Database of Shoah Victims' Names), and the **USHMM** Holocaust
  Survivors and Victims Database record for that person, each with a link —
  or an explicit *not found* / *ambiguous* status. A namesake is never merged
  without a matching birth year.

## Data downloads

`data/deaths.csv`, `data/deaths.json`, `data/deaths.sqlite` — the full database,
one row per act.

## Source

Original scans: Szukaj w Archiwach,
[unit 39731697](https://www.szukajwarchiwach.gov.pl/jednostka/-/jednostka/39731697)
(171 scans, public). Every entry on this site names its scan number so the
original can be checked.

## Method, in brief

1. All 171 scans downloaded from Szukaj w Archiwach.
2. The typed alphabetical index at the front of the book (scans 3–22) was
   transcribed as an independent name/act-number checklist.
3. Each register page was transcribed with a vision model prompted for the
   fixed Polish act formula, returning both structured fields and a verbatim
   Polish transcription of each act.
4. Verification: every number (age, death date, death hour, registration date)
   was re-parsed from the transcribed Polish number-words by a deterministic
   parser and compared with the structured fields; every name was compared
   against the book's typed index. Disagreements were re-read from zoomed
   crops of the original scans before being settled.
5. Hebrew dates computed with pyluach. The yahrtzeit is the Hebrew month/day
   of the death date.
6. Fate cross-checks were matched on name + birth year derived from the
   recorded age; DÖW matches were cross-checked against USHMM, whose
   "Österreichische Opfer des Holocaust" records carry the DÖW id as
   "Other ID".
7. A ±2-year reconciliation pass then re-examined the ambiguous results:
   where exactly one candidate's birth year falls within two years of the
   register-implied year (and the given name is compatible), the result is
   shown as a **probable match**, with the basis stated — never silently
   as a confirmed match. The same review demoted strict "found" results
   whose candidate proved to be a different person (same surname and age,
   incompatible given name, e.g. a spouse); those now read as ambiguous
   with the near-miss record named.
8. Birthplaces are shown as recorded; a standardized form (`birthplace_std`)
   groups spelling and language variants of the same place for filtering.
   Only confident identifications are grouped (e.g. Bardejov / Bardejów /
   Bardeov / Bardiów; Wiedeń = Vienna; Presburg / Pressburg = Bratislava).
   Doubtful cases (bare "Nowe Miasto", "Józefów", "Berdejsz") are left
   unmerged.

Birthplaces, ages, and causes are reproduced **as recorded in 1942** — the
register sometimes differs from other sources (it records Josef Bermann as
born in Vienna; his family and marriage records say Wiznitz). The register is
quoted, not corrected. Where an act names only the place a person was
deported *from* and no birthplace, the birthplace is shown as not recorded;
the deportation origin remains visible in the transcription.

The register contains 590 acts. Act number 310 was never used — the book's
own index leaves it blank and the acts jump from 309 to 311 — so no entry
exists for it.

## Caveats

- Handwriting transcription is fallible. The Polish transcription of each act
  is included so any field can be checked against the words, and the scan
  number points to the original image.
- "Not found" in a fate database means no matching record was found there on
  the date checked; it is not proof about a person's fate beyond this book —
  this book itself records that they died in Opole in 1942.

Compiled by Moshe Berman.

## Site features (added 2026-10-30)

- Trilingual interface: English, Deutsch, Polski (sidebar switcher).
- Register/Statistics views in a floating pinned sidebar (bottom bar on
  mobile). Statistics include multi-facet charts: age groups over time,
  cause of death over time, and age groups by cause of death, plus a
  glossary of the recorded causes. Causes are displayed in the active
  language; the recorded Polish wording is kept in the data and shown on
  each entry.
- Filters: search, birthplace (standardized), age group, gender, cause of
  death (grouped), fate recorded, yahrtzeit month, sort, page size.
- The register table carries a subtle fate dot per database (filled =
  found, half = probable, pale = ambiguous, ring = not found), and each
  row opens a detail page (›).
- Witness names are standardized in the build (`canon_witness` in
  work/build_db.py): the three regular witnesses' many spellings and both
  name orders are grouped under Mechel Frydman, Moszek Fajersztajn, and
  Oskar Hirschensohn, corroborated by their stable occupations in the
  acts. All other names are kept as recorded. Witness occupations are no
  longer displayed.
