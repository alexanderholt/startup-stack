# Brand Review Checklist

> **This checklist is evaluation structure, not company content.**
> It references sections in the brand docs (`brand/brand-tone.md` etc.)
> by name. If your brand docs use different section names, update the
> references below to match.

Evaluate the target against each applicable section. Not every section
applies to every review — skip sections that don't apply and note which
were skipped.

## 1. Brand Identity & Consistency
- Compare the target's tone and presentation against the voice description in `brand-tone.md` ("What We Sound Like" / "What We Don't Sound Like"). Does it match?
- Compare against other company materials you can access. Is the treatment consistent?
- Check the tone-by-context guidance in `brand-tone.md`. Is the tone appropriate for this specific medium (website, email, lender doc, investor materials)?

## 2. Voice & Tone
- Check the target against the voice-per-context section of `brand-tone.md`. Does the writing match the specified voice for this context?
- Check for overselling, over-explaining, or performing expertise. Compare against the "What We Don't Sound Like" examples.
- Read the target as if you are the defined audience. Would you trust this person? Would you keep reading?

## 3. Terminology & Precision
- Check every industry/regulated term against the "Words We Use" list in `brand-tone.md`. Flag incorrect usage.
- Check for any term on the "Words We Avoid" list in `brand-tone.md`. Flag every instance.
- Check that company-specific terms (product names, pricing terms, feature descriptions) are used consistently with how they appear in the brand docs.

## 4. Audience Awareness
- Check the target audience definition in `brand-tone.md`. Is the content calibrated to that expertise level — not too simple, not too jargony for the wrong audience?
- Apply the "forward test": based on the audience description, would this reader share it with a peer without qualifying it?
- Check for time-wasting patterns: filler paragraphs, repeated points, multiple CTAs competing for attention. Reference the email/outreach guidance if applicable.

## 5. Visual Design & Context Fit
- This section applies when reviewing HTML, CSS, or rendered screenshots. Skip for plain text, markdown, or email copy.
- Check color values, font declarations, and spacing against the visual guidelines in `brand/` (if available).
- Evaluate whether light/dark mode, density, and formality are appropriate for the audience and medium — reference the audience definition in `brand-tone.md`.
- Check logo usage, brand asset placement against any visual guidelines docs in `brand/`.
- Check contrast and readability.
- If reviewing source code (HTML/CSS), evaluate the visual intent from the code. If reviewing images or screenshots, use image reading capability. If neither is available, state that visual review was not possible for this target format.

## 6. Structure & Information Hierarchy
- Check against the "explain the why before the what" and "no fluff paragraphs" guidance in `brand-tone.md`.
- Does the reader reach the main point within the first 2-3 sentences?
- Is information organized the way the target audience would think about it?
- Are CTAs clear and singular?

## 7. Honesty & Trust Signals
- Check every factual claim. Is it substantiated or at least qualified?
- Check for missing disclosures: beta status, rules not yet finalized, features not yet built. Reference the "be honest about what we don't know" guidance in `brand-tone.md`.
- Flag anything that gets ahead of where the product actually is.

## Minimum Severity Guidance

| Section | Minimum severity |
|---|---|
| Terminology & Precision (prohibited words, wrong terms) | Critical |
| Honesty & Trust Signals (unsubstantiated claims) | Critical |
| Voice & Tone (wrong tone for context) | Warning |
| Audience Awareness (miscalibrated expertise level) | Warning |
| Brand Identity & Consistency (inconsistent with brand) | Warning |
| Visual Design & Context Fit (inconsistencies) | Suggestion |
| Structure & Information Hierarchy (suboptimal organization) | Suggestion |

These are minimum severities — escalate based on the specific violation.
A Voice & Tone issue that makes the company sound like a vendor pitch
is Critical, not Warning.
