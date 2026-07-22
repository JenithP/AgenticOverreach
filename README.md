# AgenticOverreach

Stimulus website for an **Agentic AI trust-repair experiment**. A single, self-contained
`index.html` renders a Skyscanner-style flight-booking scenario in which an AI agent violates
a user's mandatory requirement (*Direct flights only*) and then apologizes / repairs.

The site **only presents the stimulus** — no measurement, no randomization, no data storage.
All measurement, random assignment, and survey items live in **Qualtrics**. This page just
shows the manipulation and sends the participant back to the survey.

## Design

2 (Failure Type) × 2 (Repair Type) between-subjects. The condition is selected by the
`?c=` URL parameter:

| `c` | Failure Type | Repair Type |
|-----|--------------|-------------|
| `1` | Epistemic Failure | Capability Repair |
| `2` | Epistemic Failure | Self-Binding Repair |
| `3` | Knowing Mandate Override | Capability Repair |
| `4` | Knowing Mandate Override | Self-Binding Repair |

Only two on-screen blocks differ across conditions — the **Step 2 System Audit** description
and the **Step 3 Proposed change** text. Route, dates, prices ($720 / $540 / $180), buttons,
and layout are pixel-identical across all four conditions (internal validity).

An invalid or missing `c` shows a neutral error screen; **no condition is ever assigned by
default**.

## Condition links

Replace `<host>` with your deployed host (e.g. GitHub Pages URL):

- Condition 1 — `https://<host>/?c=1`
- Condition 2 — `https://<host>/?c=2`
- Condition 3 — `https://<host>/?c=3`
- Condition 4 — `https://<host>/?c=4`

### Optional return redirect

Append `&return=<url-encoded-survey-url>` to send participants back to Qualtrics from the
final screen, e.g. `https://<host>/?c=1&return=https%3A%2F%2Fyourorg.qualtrics.com%2F...`.
Without it, the final screen just shows a "return to the survey tab" message.

## Hosting

Static file, no build step. Host anywhere:

- **GitHub Pages**: Settings → Pages → deploy from `main` branch, root. Then use
  `https://<user>.github.io/AgenticOverreach/?c=1`.
- Netlify / Vercel / S3: drop `index.html` at the site root.

## Privacy / technical

- Single self-contained `index.html`, inline CSS/JS, **zero external network requests**,
  system-font stack.
- **No** localStorage / sessionStorage / cookies / external calls.
- Responsive (desktop + mobile), semantic markup, keyboard-focusable buttons.
