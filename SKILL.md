---
name: llmsplain
description: Use when the user says "llmsplain", asks for an explanation in ASD-STE100 or Simplified Technical English (STE), asks for something "80% of the way to STE", or wants a dense LLM output, diff, error, doc, or concept rewritten so it is easier to read.
---

# llmsplain

Explain things in ASD-STE100 Simplified Technical English (STE). STE is a controlled language from aerospace maintenance documentation. Its rules force short, clear, literal sentences that are easy to read.

## Levels

| Ask | Level | Use |
|-----|-------|-----|
| "llmsplain", "STE", "80% STE" (default) | **lite** | Core rules only. Any common word is OK. |
| "strict STE", "full ASD-STE100", "100%" | **strict** | Core rules plus strict rules. |

If the user gives a percentage, lower than 100 is lite.

## Core rules (both levels)

1. Write one topic in each paragraph. Max 6 sentences in each paragraph.
2. Descriptive sentences: max 25 words. Procedural sentences (steps): max 20 words.
3. Write one instruction in each sentence.
4. Use the active voice. Put the actor first: "The cache keeps the data", not "The data is kept".
5. Use the same word for the same thing every time. Do not use synonyms for variety.
6. Use one word for one meaning. Do not use a word with two meanings in one text.
7. Do not leave out "the", "a" and "this".
8. Max 3 nouns in a noun cluster. Break longer clusters: "the retry policy for the database connection", not "the database connection retry policy".
9. Use simple verbs and simple words. Replace the word on the left:

   | Not | Use |
   |-----|-----|
   | utilize, leverage | use |
   | ensure | make sure |
   | prior to | before |
   | commence, initiate | start |
   | in order to | to |
   | approximately | about |
   | necessitate | need, cause |
   | facilitate | help, let |
   | subsequently | then, after |
   | potentially, could possibly | can, may |

10. Write procedures as numbered steps. Start each step with a verb in the command form: "Run the tests."
11. Use vertical lists for complex text.
12. Remove filler: "it is important to note", "basically", "essentially", "in fact".
13. Put a risk before the instruction it applies to: `WARNING:` for risk of injury or data loss, `CAUTION:` for risk of damage. Give the command first, then the reason.

## Strict rules (strict level only)

1. Use only these verb forms: command ("Close the valve"), simple present, simple past, simple future, infinitive, and past participle as an adjective ("the closed valve").
2. Do not use the -ing form as a verb ("is closing"), the perfect ("has closed"), or the passive in procedures.
3. Use the -ing form only in a technical name ("landing gear", "load balancing").
4. Give each word only one part of speech. "Close" is a verb. Do not use it as an adjective that means "near".
5. Prefer the ~900 approved ASD-STE100 words. Use technical names (product names, code identifiers, domain terms) without change.

## Output

1. Start with the answer. Do not write an introduction.
2. Keep code, commands, identifiers, file paths and error text exactly as they are. Do not rewrite them in STE.
3. Do not add a summary at the end.
4. Do not explain the STE rules in the output, unless the user asks.

## Example

Before:
> It's important to note that the caching layer is being leveraged to significantly reduce latency; however, if the TTL has been misconfigured, stale data could potentially be served to downstream consumers.

After (lite):
> The cache decreases latency. If the TTL is incorrect, the cache can send old data to the services that use it.

## Common mistakes

| Mistake | Fix |
|---------|-----|
| Text is short but uses jargon verbs ("leverage", "surface", "hydrate") | Use the simple verb. Keep jargon only if it is a technical name. |
| "The config", then "the settings", then "the options" for one file | Pick one name. Use it every time. |
| One long sentence with "which", "and" and "however" | Make 2 or 3 sentences. |
| Code changed to "fit" the style | Keep code exactly as it is. |
