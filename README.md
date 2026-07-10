# mercilint 🔥

**Brutal code roasts where every insult comes with a fix.**

A Claude Code skill that reviews your uncommitted diff with the fury of a celebrity head chef — and the rigor of a senior reviewer. Every burn is severity-ranked and maps to a concrete fix. Funny on the surface, strict underneath.

> "You caught the error and threw it in the BIN?! That's not error handling, that's hiding the burnt steak under the garnish and praying the customer's drunk!"

## Install

```bash
git clone https://github.com/kpab/mercilint ~/.claude/skills/roast
```

That's it. No build, no config, no dependencies — it's a single Markdown skill.

## Usage

Inside any git repo with uncommitted changes:

```
/roast
```

The chef inspects your working diff (`git diff HEAD`) and sends back what deserves to be sent back.

## What it looks like

You plated this:

```go
const apiKey = "sk_live_51Hxq2m..."

func Charge(db *sql.DB, customerID string, amountCents int) error {
	_, err := db.Exec("INSERT INTO charges (customer_id, amount) VALUES ('" + customerID + "', " + fmt.Sprint(amountCents) + ")")
	if err != nil {
		// TODO: handle later
	}
	return nil
}
```

The chef responds:

> ### 🤢 RAW · `payment.go:14` — SQL injection served table-side
>
> "You RIPPED OUT the parameterized query and started gluing raw customer input straight into the SQL?! That's not cooking, that's letting the customers walk into the kitchen and season the pot themselves!"
>
> **Fix**: restore placeholders:
> `db.Exec("INSERT INTO charges (customer_id, amount) VALUES (?, ?)", customerID, amountCents)` — never build SQL by string concatenation.
>
> ### 🤢 RAW · `payment.go:8` — live API key plated in the source
>
> "A `sk_live_` key sitting in the repo — WHAT IS THIS?! You've written the safe combination on the specials board!"
>
> **Fix**: delete the constant, load it from the environment (`os.Getenv("STRIPE_API_KEY")` or your secrets manager), and **rotate the key now** — once committed, it's compromised.
>
> ---
> **The Verdict**: 2 RAW, 1 BURNT. You took a perfectly seasoned payment function and turned it into an injection buffet with the till keys taped to the door. Service is SUSPENDED until the RAW ones are fixed. 🤢2 🔥1

## The severity scale

| Label | Emoji | Meaning |
|-------|-------|---------|
| RAW | 🤢 | Critical — bugs, data loss, security. This plate goes back. |
| BURNT | 🔥 | High — will break under real load / real inputs. |
| BLAND | 🧂 | Medium — works, but sloppy: naming, duplication, structure. |
| GARNISH | 🍽️ | Low — nitpicks. Mentioned only if worth the breath. |

## House rules

The joke is the delivery mechanism. The review is real.

- **No fix, no roast.** Every burn ends in a concrete fix — a code snippet, an exact rename, or a precise instruction with `file:line`. A joke without a fix is out of spec.
- **Roast the dish, not the cook.** The code gets destroyed. You don't.
- **No invented problems.** The technical claim must be correct before the metaphor is applied. If your diff is genuinely clean, the chef admits it — grudgingly. ("...Fine. It's seasoned. Get out of my kitchen.")
- **Worst first.** Critical findings lead; nitpicks are skipped entirely when there's real fire to fight.

## Why

Code review feedback lands harder when you actually want to read it. mercilint wraps a strict, severity-ranked review in a voice you'll quote to your teammates — and every quote points at a line you can fix right now.

## Requirements

- [Claude Code](https://claude.com/claude-code)
- A git repo with uncommitted changes (the chef refuses to inspect an empty plate)

## License

[MIT](LICENSE)
