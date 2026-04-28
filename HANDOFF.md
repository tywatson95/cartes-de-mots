# Cartes de Mots — Project Handoff

## What this is

A French flashcard web app built as a single HTML file. Designed for Ty, a Katonah Yoga teacher based in Paris, working at B1 level toward B2. Built collaboratively with Claude on Claude.ai over a long conversation.

The user (Ty) is not a developer. He needs deployment guidance that assumes zero technical background. The other person on this account (Arno, his husband) is a developer at MIT, but Ty is the one using this app and the one you'll likely be talking to.

## Current state

Single file: `cartes-de-mots.html`. Self-contained — no build step, no dependencies, no server. Just open in a browser.

## Immediate goals

1. Initialise git in the project directory
2. Create a GitHub repository (Ty does not yet have a GitHub account or may need to create one)
3. Push the file
4. Enable GitHub Pages so it has a public URL
5. Help Ty add it to his iPhone home screen

## Architecture

- Vanilla HTML/CSS/JS in one file
- `localStorage` for persisting user-added cards, edits, and deletions to default decks
- `SpeechSynthesisUtterance` for French audio (uses browser-native voice, prefers `fr-FR`)
- Card flip via CSS 3D transforms
- Spaced repetition is light: "Again" puts the card back ~3 positions ahead in the queue, "Hard" and "Got it" advance. No SM-2 algorithm — deliberate simplicity.

## Decks (in order)

1. **Yoga** (~50 cards) — grounded in Katonah Yoga concepts. Five themes: Magic Square geometry & orientation, Five Elements (Wu Xing), TCM organ systems, Daoism & energy, Jung & psychoanalytic. Plus practical anatomy/cueing verbs. **No generic wellness platitudes** — this was an explicit design constraint.
2. **Phrases clés** (~26 cards) — B1+ conversational chunks with construction tags
3. **Questions** (~20 cards) — asking and being asked
4. **Quotidien** (~22 cards) — Paris café/daily life vocabulary
5. **Conjugaisons** (~108 cards) — verb conjugation drilling. Verbs in frequency order: être, avoir, faire, aller, dire, pouvoir, vouloir, savoir, devoir, voir, venir, prendre, mettre, falloir, croire, partir + finir, parler as regular models. Tenses: présent, passé composé, imparfait, futur simple, conditionnel, subjonctif, plus-que-parfait. Format: front shows `(pronoun) infinitive` + tense tag, back shows the form + example sentence.
6. **À compléter** (~30 cards) — sentence completion. Front: sentence with blank + infinitive hint. Back: the form + full sentence. Weighted toward subjunctive triggers (Ty's identified weak spot).
7. **Mes mots** — empty, for user-added cards

## Grammar tag philosophy

After iteration, tags are **construction-focused**, not part-of-speech labels. So `+ subjonctif`, `+ infinitif`, `+ de + infinitif`, `si + plus-que-parf., cond. passé`, etc. For verbs in non-conjugation decks, format is `je [form] · j'ai [past participle]` with `(irreg.)` flag on irregular ones. Cards that don't need tags have empty grammar fields — visual quietness is the design goal.

## Design language

- Cream/warm-earth palette (defined as CSS variables: `--cream`, `--warm`, `--sand`, `--clay`, `--dark`, `--accent`, `--green`, `--rust`)
- Cormorant Garamond serif for French + display, DM Sans for UI
- Mobile-first: max-width 380px throughout, designed to live on iPhone home screen via "Add to Home Screen"
- Dark card back (`--dark`) with cream text on flip
- Quiet, contemplative feel — no gamification, no streaks, no points

## What Ty has asked for that's already done

- Audio pronunciation (SpeechSynthesis)
- Browse mode (scroll all cards, edit/delete inline)
- Add cards with category dropdown
- Edit existing cards (including default ones)
- Persistent storage across sessions
- Construction-focused grammar tags
- Conjugation drilling deck
- Sentence completion deck

## Things that may come up next

- Ty may want export/import so cards sync between devices (currently localStorage is per-browser)
- He may want more yoga vocabulary as he discovers his teaching gaps in French
- Spaced repetition could be made more sophisticated if he sticks with it (SM-2 / FSRS)
- He may want a way to filter conjugation cards by tense
- He's iPhone-only on the consumer side; Arno is the technical one but this app is for Ty

## How Ty likes to work

Direct, honest, pushes back when something sounds off. Wants pedagogical reasoning explained, not just feature lists. Gets frustrated by platitudes and generic AI-speak. Yoga/Daoist sensibility — quietness, intentionality, no clutter.

He is not a developer. Walk him through everything step-by-step in plain language. Don't assume he knows what `git init` does — explain it. He uses a Mac. Arno's Mac is set up for development (`agrobler` is Arno's MIT username on the machine) so the development tools likely exist already, but Ty himself has not used them.

## File location

The file is in the same directory as this handoff doc when you start.
