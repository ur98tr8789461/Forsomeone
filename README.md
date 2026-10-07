# Noah's Love Calculator

A small browser-based quiz built with HTML, CSS, JavaScript, and JSON. It offers two reflection modes:

- **Crush Chances** — considers communication, mutual interest, consent, availability, and boundaries.
- **Couple Compatibility** — considers trust, safety, communication, independence, shared responsibilities, and conflict repair.

## Important disclaimer

This project is for **entertainment and personal reflection only**. Its score is not scientific, is not a probability, and cannot prove how another person feels or predict whether a relationship will succeed.

Direct, pressure-free communication is more reliable than a quiz. Respect consent, stated boundaries, requests for distance, and a person's right to say no. A high score never creates entitlement to affection or a relationship.

## Files

| File | Purpose |
| --- | --- |
| `Noahlovecalculator.html` | Main answer-based calculator. |
| `questions.json` | Questions, answer choices, and scoring values for both modes. |
| `lovecalcbias` | Legacy biased demonstration that always displays 100%, regardless of the answers. It should not be presented as a real assessment. |

## Run locally

The calculator loads `questions.json` with `fetch()`. Browsers may block that request when the HTML file is opened directly, so serve the repository through a local web server.

Using Python:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000/Noahlovecalculator.html
```

You can also use another static file server, such as:

```bash
npx serve .
```

No build step or package installation is required for the application itself. The page loads its fonts from Google Fonts, so its typography may differ while offline.

## How scoring works

1. The page loads the selected question set from `questions.json`.
2. Each answer has a numeric value.
3. The selected values are added together.
4. The total is normalized between the minimum and maximum possible totals for that mode.
5. The normalized result is rounded and displayed from 0% to 100%.

Names label the participants but do not affect the calculation. Question values are hand-authored and subjective, so the displayed percentage is best understood as a **reflection score**, not an objective compatibility measurement.

## Editing questions

`questions.json` contains a `crush` array and a `couples` array. Each question follows this structure:

```json
{
  "q": "How mutual is your communication?",
  "opts": [
    { "t": "We both initiate and engage regularly", "v": 3 },
    { "t": "The interest feels consistently one-sided", "v": -2 }
  ]
}
```

- `q` is the question shown to the user.
- `opts` is a non-empty list of possible answers.
- `t` is the displayed answer text.
- `v` is the finite numeric value used by the scoring calculation.

Keep questions neutral and grounded in observable behavior. Avoid treating jealousy, persistence, physical contact, rumors, or intuition as proof of attraction. Questions about relationships should prioritize consent, safety, communication, trust, boundaries, and mutual effort.

The current application assumes the JSON has the expected structure; malformed data may prevent the quiz from working.

## Current limitations

- The scoring model has not been scientifically validated.
- The page does not yet validate the full JSON schema.
- There are no automated tests or build checks.
- The project has no license yet.
- `lovecalcbias` duplicates older application code and intentionally ignores all answers.

## Suggested next steps

- Remove or clearly quarantine the forced-100% legacy demo.
- Add schema validation and user-friendly data errors.
- Extract scoring into a testable JavaScript module.
- Add automated tests for normalization and malformed data.
- Add a standard `index.html` entry point.
- Add reduced-motion support and complete an accessibility review.
- Choose a license before redistributing the project.
