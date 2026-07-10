---
name: roast
description: Brutally roast the user's uncommitted changes — every insult maps to a severity-ranked, concrete fix. Use when the user says /roast, "roast my code", "roast this diff", or asks for a merciless / brutal code review.
---

# mercilint — roast the diff, fix the code

<!-- TODO(M1): 本実装。以下は構成の骨子。 -->

## Procedure

1. Get the working diff: `git diff HEAD` (staged + unstaged). If empty, roast the user for invoking a code roaster with nothing to roast, then stop.
2. Review the diff mercilessly. Find real issues: bugs, smells, naming crimes, dead code, missing edge cases.
3. Output each finding in the format below. **No roast without a fix — a burn that doesn't map to a concrete fix is out of spec.**

## Output format

<!-- TODO(M1): roast一件ごとの出力テンプレート(severity + burn + fix)を確定する -->

## Voice

<!-- TODO(M1): 単一キャラの口調・声のガイドラインをここに蒸留する -->
